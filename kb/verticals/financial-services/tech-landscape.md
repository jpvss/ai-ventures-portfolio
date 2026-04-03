---
title: "Financial Services — Tech Landscape"
type: tech-landscape
vertical: financial-services
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [financial-services, tech-landscape, APIs, BCB, SCR, open-finance, data-sources]
---

# Financial Services — Tech Landscape

## Data Sources Inventory

### Government and Regulatory Data

| Source | Data Available | Access Method | Cost | Freshness | Notes |
|--------|---------------|---------------|------|-----------|-------|
| **BCB/SCR** | Credit operations (borrower exposure, risk classification, default history) | API (requires BCB authorization + borrower consent) | Free (institutional) | Monthly (D+15 reporting) | Primary credit information system; mandatory for all regulated lenders |
| **Receita Federal (CNPJ)** | Company registration, QSA (partners), CNAE, capital social, situação cadastral | API (ReceitaWS, CNPJá) or bulk download | Free (bulk) or R$0.05–R$0.50/query (API) | Weekly bulk updates | Essential for SME/corporate credit; QSA reveals beneficial ownership |
| **PNCP (Portal Nacional de Contratações Públicas)** | Government contract awards, amendments, contractor performance | API (REST) | Free | Daily updates | Cross-vertical with licitaleads; key credit signal for SME/factoring |
| **FIPE (Fundação Instituto de Pesquisas Econômicas)** | Vehicle price tables (new + used), historical price curves | API | R$0.10–R$1.00/query | Monthly updates | Standard for vehicle collateral valuation; limited to price tables |
| **IBGE** | Economic indicators, price indices, demographic data, regional statistics | API (SIDRA) | Free | Varies (monthly to annual) | Context data for regional credit risk; property price indices |
| **Detran (state-level)** | Vehicle registration, liens, theft alerts, accident history | Varies by state (some APIs, some screen scraping) | R$2–R$10/query | Near real-time | Critical for vehicle lending fraud detection; fragmented across 27 states |
| **PJe / TJSP / Court systems** | Judicial proceedings, lawsuits, bankruptcy filings | Varies (some APIs, mostly scraping) | R$1–R$5/query (via aggregators) | Daily updates | Negative credit signal; important for large exposures |
| **CAGED / eSocial** | Employment records, salary data (with authorization) | API (government) | Free (institutional) | Monthly | Income verification for payroll lending |

### Credit Bureaus and Data Providers

| Source | Data Available | Access Method | Cost | Notes |
|--------|---------------|---------------|------|-------|
| **Serasa Experian** | Credit score, payment history, negative records, credit inquiries, positive cadastro | REST API | R$1–R$5/query depending on product | Largest bureau in Brazil; most comprehensive negative data |
| **SPC/Boa Vista** | Credit score, negative records, check history, protest records | REST API | R$0.50–R$3/query | Strong in retail/consumer segment; cheaper than Serasa for basic queries |
| **Quod** | Positive cadastro (payment history), credit score based on positive data | REST API | R$0.50–R$2/query | BCB-mandated positive credit bureau; growing data coverage |
| **BigData Corp** | Alternative data (social media, web presence, device data, behavioral) | REST API | R$0.10–R$1/query | Useful for thin-file borrowers; enrichment layer |
| **Neoway / Datalake** | Company data enrichment, litigation, media monitoring | REST API | R$1–R$10/query | Enterprise-grade company intelligence; expensive but comprehensive |

### Open Finance APIs

| Phase | Data Available | Status | Key Endpoints |
|-------|---------------|--------|---------------|
| **Phase 1** | Product/channel information (public) | Live | /products, /channels |
| **Phase 2** | Account data, transactions, credit cards | Live | /accounts, /transactions, /credit-cards |
| **Phase 3** | Payment initiation (PIX, TED) | Live | /payments, /pix |
| **Phase 4** | Credit data, investments, insurance, FX | Expanding | /loans, /financings, /investments |

**Technical details:**
- Authentication: OAuth 2.0 with FAPI (Financial-grade API) security profile
- Consent: PKCE + dynamic client registration
- Data format: JSON (BCB-standardized schema)
- SLA: 99.5% availability; response time <1s for 95th percentile
- Rate limiting: varies by institution (typically 300–1,000 requests/minute)

## Core Systems in Mid-Market

### Typical Technology Stack (Fintech de Crédito)

```
Frontend: React/Next.js or Flutter (mobile)
    ↓
API Gateway: Kong, AWS API Gateway, or custom
    ↓
Backend: Node.js, Python (FastAPI/Django), or Go
    ↓
Core Banking / Loan Management:
├── Custom-built (Python/Java) — 40% of fintechs
├── BaaS platform (QI Tech, Dock, Zoop) — 30%
├── Vendor LMS (Mambu, Pismo, Technisys) — 20%
└── Spreadsheets + manual processes — 10% (factorings)
    ↓
Database: PostgreSQL (primary), Redis (cache), MongoDB (documents)
    ↓
Data Warehouse: BigQuery, Snowflake, or Redshift (if they have one — 30% don't)
    ↓
Bureau Integrations: Direct API or via aggregator (e.g., Data Stone, Neoway)
    ↓
Reporting: Metabase, Looker, or Excel (SCR often manual)
```

### Typical Technology Stack (Factoring)

```
Frontend: Custom web app or legacy desktop app
    ↓
Core System:
├── Specialized factoring software (e.g., Fator, Keevo) — 50%
├── ERP adapted for factoring (TOTVS, SAP B1) — 30%
└── Excel/Google Sheets — 20%
    ↓
Bureau: Manual Serasa queries (no API integration)
    ↓
Data: No warehouse; data in operational database or spreadsheets
    ↓
Reporting: Excel; SCR often outsourced to accounting firm
```

### BaaS Providers (Infrastructure Partners, Not Competitors)

| Provider | Specialization | API Quality | Credit Modules | Notes |
|----------|---------------|-------------|----------------|-------|
| **QI Tech** | Full BaaS; SCD/SEP infrastructure | High | Basic scoring module | Good partner — serves fintechs that need our intelligence layer |
| **Dock** | Payment processing, card issuing, BaaS | High | Minimal | More payments-focused; less credit |
| **Zoop** | Payment processing, marketplace payments | Medium | None | Payments-only; complementary |
| **Bankly** | Digital banking infrastructure | Medium | Basic | Newer entrant; growing |
| **Pismo** | Core banking platform | High | Some | More enterprise; Visa-acquired |

## Integration Patterns

### Bureau API Integration Pattern

```python
# Intelligent bureau routing — query cheapest first, escalate for borderline
class BureauRouter:
    def score(self, cpf_cnpj):
        # Step 1: Query cheapest bureau (SPC/Boa Vista, ~R$0.50)
        spc_result = self.query_spc(cpf_cnpj)
        
        # Step 2: If clear approve or reject, stop here
        if spc_result.score > 800 or spc_result.has_negatives:
            return self.format_result(spc_result)
        
        # Step 3: Borderline — query Serasa for enrichment (~R$3.00)
        serasa_result = self.query_serasa(cpf_cnpj)
        
        # Step 4: Still borderline — query Quod positive data (~R$1.00)
        if self.is_borderline(serasa_result):
            quod_result = self.query_quod(cpf_cnpj)
            return self.combine_scores(spc_result, serasa_result, quod_result)
        
        return self.combine_scores(spc_result, serasa_result)
```

**Cost optimization:** This pattern reduces average bureau cost from R$7–R$10/query (all bureaus) to R$1.50–R$3/query, saving 50–70%.

### SCR Integration Pattern

```
BCB SCR Query Flow:
1. Borrower provides authorization (digital consent)
2. System submits SCR query via BCB API (CCS/SCR channel)
3. BCB returns: total exposure, # of institutions, risk classification, default history
4. System parses response into structured features for scoring model
5. SCR data cached for 30 days (BCB guideline)

BCB SCR Reporting Flow:
1. Extract credit operations from loan management system (monthly)
2. Apply BCB risk classification rules (AA through H)
3. Generate SCR file in BCB-required schema (XML/CSV)
4. Validate against BCB validation rules (200+ checks)
5. Submit via BCB reporting channel (PSTA/STA)
6. Monitor for rejection/correction requests
7. Archive submission for audit trail
```

### Open Finance Integration Pattern

```
Consent Flow:
1. Customer initiates consent in your app
2. Redirect to data-holding institution for authentication
3. Customer authorizes data sharing (FAPI/PKCE)
4. Receive consent ID and access token
5. Store consent metadata (scope, expiry, revocation callback)

Data Retrieval Flow:
1. Use access token to query institution APIs
2. Retrieve account data, transactions, credit data
3. Normalize data to internal schema (institutions vary)
4. Categorize transactions (income, expenses, loans, transfers)
5. Extract features for credit scoring
6. Store in data lake with consent linkage for LGPD compliance
7. Set up refresh schedule (consent allows periodic access)
```

## Infrastructure Recommendations

### Recommended Tech Stack for JP Ventures Implementations

| Component | Recommended | Alternative | Rationale |
|-----------|-------------|-------------|-----------|
| **Data Lake** | Snowflake or BigQuery | Databricks, Redshift | Managed; scales; SQL-friendly for analysts |
| **Orchestration** | Airflow (managed) or Prefect | Dagster | Mature; good for ETL/ELT pipelines |
| **ML Platform** | MLflow + SageMaker or Vertex AI | Custom | Experiment tracking + model serving |
| **LLM** | Claude API (Anthropic) or GPT-4o | Open source (Llama) for sensitive data | Best reasoning for credit memos and contract analysis |
| **Feature Store** | Feast or Tecton | Custom on Redis | Feature consistency between training and serving |
| **API Gateway** | Kong or AWS API Gateway | Custom | Rate limiting, authentication, monitoring |
| **Monitoring** | Evidently AI (ML monitoring) + Grafana | Custom | Drift detection, model performance tracking |
| **Secrets/Config** | AWS Secrets Manager or Vault | Azure Key Vault | Bureau API keys, BCB certificates |

### Data Architecture Pattern

```
Sources → Ingestion → Raw Layer → Processed Layer → Feature Store → Models → Serving
  ↓           ↓           ↓             ↓               ↓            ↓         ↓
Bureau     Airflow    S3/GCS      Snowflake/BQ       Feast      MLflow    FastAPI
SCR        APIs       Parquet     dbt transforms     Redis      SageMaker REST API
PNCP       Webhooks   JSON        Quality checks     Online+    Vertex    Dashboard
Receita    Batch      CSV         Deduplication       Offline    Claude    LMS
Open Fin   Stream                 Enrichment                    API       CRM
```

### Security and Compliance Requirements

| Requirement | Implementation |
|-------------|---------------|
| LGPD data classification | Tag all PII fields; implement access controls by classification level |
| Encryption at rest | AES-256 for all databases and storage; bureau data and SCR data encrypted |
| Encryption in transit | TLS 1.3 for all API communications; mTLS for BCB connections |
| Access logging | All data access logged with user, timestamp, purpose; 5-year retention |
| Consent tracking | Open Finance consent linked to all derived data; revocation triggers data deletion |
| BCB security requirements | Follow BCB Resolução 4.893 security requirements for Open Finance participants |
| Pen testing | Annual penetration testing; quarterly vulnerability scanning |
| Data retention | Credit data: 5 years (BCB); consent data: duration of consent + 1 year; bureau data: 30-day cache |

## API Rate Limits and Cost Planning

### Monthly Cost Estimate (Per Client)

| Data Source | Queries/Month | Cost/Query | Monthly Cost |
|-------------|--------------|------------|-------------|
| SPC/Boa Vista | 500 (all applications) | R$0.50 | R$250 |
| Serasa | 200 (borderline only) | R$3.00 | R$600 |
| Quod | 100 (thin-file only) | R$1.00 | R$100 |
| Receita Federal | 500 (all applications) | R$0.10 | R$50 |
| PNCP | Unlimited (bulk ingestion) | Free | R$0 |
| SCR | 500 (all applications) | Free (institutional) | R$0 |
| Open Finance | 200 (consented users) | Free (API) | R$0 |
| Cloud infrastructure | — | — | R$2,000–R$5,000 |
| LLM API (credit memos) | 500 | R$0.50 | R$250 |
| **Total** | | | **R$3,250–R$6,250/month** |

This compares to R$5,000–R$15,000/month for manual bureau queries + analyst time, representing 40–60% cost reduction.

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
