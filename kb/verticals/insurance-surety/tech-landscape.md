---
title: "Insurance & Surety Bonds — Technology Landscape"
type: tech-landscape
vertical: insurance-surety
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [insurance-surety, technology, systems, apis, data-sources, SUSEP, OPIN, FAPI]
---

# Insurance & Surety Bonds — Technology Landscape

## Common Client Systems

| System Type | Common Products | Integration Method | Data Format |
|-------------|----------------|-------------------|-------------|
| Core Policy Admin | Guidewire, Sinqia/Evertec, custom-built | REST API (newer), SQL/file export (legacy) | Proprietary schemas |
| CRM | Salesforce, custom-built | REST API | JSON/XML |
| Claims Management | Guidewire ClaimCenter, Sinqia, custom | REST API, SQL | Proprietary |
| Financial / Accounting | SAP, TOTVS, custom | REST API, flat files | Various |
| Broker Management | Agger, custom portals | Web/API | Various |
| Document Management | Various / manual | File system, OCR required | PDF, scanned images |

## Data Sources

### Public/Government APIs

| Source | Data Available | Access Method | Cost | Freshness |
|--------|---------------|--------------|------|-----------|
| **SUSEP Open Data** | Insurance market data, premium volumes, loss ratios, insurer financials | REST API / CSV download (dados.susep.gov.br) | Free | Monthly/quarterly |
| **PNCP** (Portal Nacional de Contratações Públicas) | Government procurement data, contract values, seguro garantia requirements | REST API | Free | Real-time |
| **ComprasNet** | Federal procurement data (legacy, being migrated to PNCP) | REST API | Free | Real-time |
| **Receita Federal CNPJ** | Company registration data, CNAE codes, legal status | API | Free/limited | Updated regularly |
| **CEIS/CNEP** | Sanctioned/debarred companies | REST API | Free | Real-time |
| **B3 Trillia** | Insurance data sharing platform (new partnership with CNseg) | API (emerging) | TBD | Emerging |

### Commercial Data Providers

| Provider | Data Available | Pricing Model | Integration |
|----------|---------------|--------------|-------------|
| **Serasa Experian** | Credit scores, financial risk, company data, court records | Per-query API pricing | REST API |
| **Boa Vista / Equifax** | Credit scores, financial risk, delinquency data | Per-query API pricing | REST API |
| **Court Record Databases** (PJe, state TJ systems) | Processos judiciais, litigation history | Varies by state | Web scraping / API (varies) |
| **B3** | Financial market data, company filings | Subscription | API |

### Client Internal Data

Typical internal data sources we need access to during engagements:
- **Policy administration database**: All active/historical policies, premiums, coverage, terms
- **Claims management system**: Claims history, resolution data, payout amounts, documentation
- **Underwriting records**: Tomador applications, credit analyses, approval/rejection decisions with rationale
- **CRM data**: Broker relationships, client communications, pipeline
- **Financial data**: Premium collections, reserves, reinsurance cessions
- **Document repositories**: Editais, apólices, sinistro documentation (often unstructured PDF/scanned)

## Integration Patterns

### Pattern 1: Credit Bureau Integration

**Source:** Serasa Experian, Boa Vista/Equifax
**Method:** REST API (paid, per-query)
**Challenges:** Rate limiting, cost management at scale, data freshness, response time for real-time underwriting
**Solution:** Caching layer with configurable TTL, batch pre-fetch for renewal pipeline, fallback between providers

### Pattern 2: SUSEP Data Integration

**Source:** SUSEP Open Data (dados.susep.gov.br)
**Method:** REST API and CSV download
**Challenges:** Data format inconsistencies, historical data gaps, schema changes
**Solution:** ETL pipeline with schema validation, automated refresh on SUSEP publication schedule

### Pattern 3: Government Procurement Data

**Source:** PNCP, ComprasNet
**Method:** REST API
**Challenges:** Data volume (millions of contracts), matching procurement to seguro garantia opportunities
**Solution:** Event-driven pipeline with NLP classification of procurement notices, automated opportunity matching

### Pattern 4: Court Record Aggregation

**Source:** PJe (national), 27 state TJ systems
**Method:** Web scraping / limited APIs (varies dramatically by state)
**Challenges:** 27 different systems with different formats and anti-scraping measures; no unified identifier
**Solution:** State-specific scrapers with CNPJ-based matching, rotating proxies, structured data normalization layer

### Pattern 5: OPIN API Implementation

**Source/Target:** OPIN ecosystem (other insurers, brokers, platforms)
**Method:** FAPI-certified APIs, mTLS, OAuth 2.0, DCR (Dynamic Client Registration)
**Challenges:** FAPI certification requirements, consent management complexity, data schema compliance
**Solution:** FAPI-compliant API gateway (leverage Finansystech/Celcoin open-as-a-service), LGPD-aligned consent orchestration, OPIN data schema validation layer

## Key Ecosystem Players (Technology)

| Player | Role | Relevance |
|--------|------|-----------|
| **Finansystech/Celcoin** | Open-as-a-service for OPIN compliance | Provides OPIN infrastructure; potential partner to accelerate OPIN Integration projects |
| **Agger** | Broker management platform | Present in 95% of Brazilian municipalities; key integration point for broker-insurer exchange |
| **Granto Seguros** | Embedded seguro garantia via API | API integrations with 15+ insurers; benchmark for digital-first distribution |
| **Brick** | AI agents for underwriting and fraud detection | 650+ clients; provides AI agents — potential competitor or complementary tool |
| **Autoinsp** | AI computer vision for inspections | Complementary technology for claims inspection automation |
| **Segarante** | Digital seguro garantia platform | Digital-first platform for seguro garantia distribution |
| **Guidewire** | Enterprise core insurance systems | PolicyCenter, ClaimCenter, BillingCenter — common client systems we integrate with |
| **Sinqia/Evertec** | Core insurance technology | Brazilian insurance technology provider — common client system |

## Recommended Tech Stack

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| Data Ingestion | Custom API connectors (Python/Node.js), OCR pipeline (Azure AI Document Intelligence) | Multi-source integration from credit bureaus, SUSEP, courts, OPIN |
| Storage | PostgreSQL (operational) + Cloud Data Lake (S3/Azure Blob) | Handle structured policy/claims data and unstructured documents |
| Processing | Python ML pipeline (scikit-learn, XGBoost, LightGBM) + Rules Engine | Credit scoring, claims prediction, compliance validation |
| Analytics | Apache Superset or Metabase + custom dashboards | Real-time operational dashboards + regulatory compliance reports |
| API Layer | FAPI-certified gateway (Kong/custom) + REST APIs | OPIN regulatory compliance + modern integration with client systems |
| Security | mTLS, OAuth 2.0, LGPD consent management platform | Regulatory requirements for OPIN, Circular 638/2021 cybersecurity, LGPD |
| NLP/AI | Azure OpenAI / Claude API for document intelligence, custom ML models for scoring | Document OCR, edital parsing, claims text analysis |
| Infrastructure | AWS or Azure (choose based on client ecosystem) | Scalable cloud infrastructure with Brazil region availability |

## Key Technical Challenges

1. **Legacy core system integration (69% barrier per CNseg/EY)**: Most mid-market insurers run policy admin systems with limited or outdated APIs. Solution: build an integration layer that adapts to each client's specific system, using database connectors, file-based exchange, or API wrappers as needed.

2. **FAPI certification for OPIN**: OPIN requires FAPI-certified APIs with mTLS and DCR. Solution: leverage Finansystech/Celcoin infrastructure or build FAPI-compliant gateway.

3. **Court record heterogeneity**: 27 state court systems with different formats, access methods, and anti-scraping measures. Solution: state-specific scrapers with unified normalization layer; start with highest-volume states (SP, RJ, MG, PR).

4. **Real-time underwriting data**: Moving from batch credit checks to real-time risk scoring requires low-latency integrations with credit bureaus and caching strategies. Solution: intelligent caching with configurable TTL, pre-fetch for renewals, fallback between providers.

5. **LGPD + OPIN dual consent**: Managing consent across both LGPD requirements and OPIN data sharing creates complexity. Solution: unified consent management platform that satisfies both regulatory frameworks simultaneously.

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
