---
title: "Real Estate — Technology Landscape"
type: tech-landscape
vertical: real-estate
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [real-estate, technology, systems, apis, data-sources, Sienge, ITBI, FipeZAP, SREI]
---

# Real Estate — Technology Landscape

## Common Client Systems

| System Type | Common Products | Market Position | Integration Method | Data Format |
|-------------|----------------|-----------------|-------------------|-------------|
| **ERP (incorporacao)** | Sienge (Softplan) | ~40% mid-market penetration | REST API (Sienge Platform API) | Structured DB, REST JSON |
| **ERP (alternative)** | UAU (TOTVS) | ~25% mid-market | TOTVS REST API framework | Structured DB, REST JSON |
| **ERP (smaller)** | Mega (TOTVS), Globaltec | ~15% combined | Varies; some API, some DB access | Varies |
| **CRM** | Vista Software | ~35% mid-market | REST API | JSON, webhooks |
| **CRM** | Hypnobox | ~15% mid-market | REST API | JSON |
| **CRM** | CV CRM (Construtora Virtual) | ~10% mid-market | REST API | JSON |
| **Accounting** | Excel / manual | ~60% for SPE consolidation | File export (CSV/XLSX) | Spreadsheets |
| **Accounting** | Dominio (Thomson Reuters) | ~20% (outsourced offices) | File export, some API | Structured DB |
| **Construction management** | Prevision, Agilean, Construct | Growing adoption | REST API | JSON, project files |
| **Document management** | Google Drive / OneDrive / email | ~70% (unstructured) | Cloud APIs | Files, PDFs |

## Data Sources

### Public/Government APIs and Systems

| Source | Data Available | Access Method | Cost | Freshness |
|--------|---------------|--------------|------|-----------|
| **ITBI municipal databases** | Property transaction values, dates, parties | Varies by municipality: web portal scraping (most), API (SP, BH, Curitiba), FOIA requests | Free (portal) / R$5K--R$20K (bulk extraction per city) | Updated per transaction; lag varies 30--90 days |
| **FipeZAP** | Property price index, listing prices, rental indices | API (subscription) | R$20K--R$80K/year depending on scope | Monthly index; daily listing data |
| **IBGE Census / setores censitarios** | Population, income, demographics, urbanization | Public API (SIDRA), bulk download | Free | Census every 10 years; estimates annually |
| **IBGE geographic mesh** | Setores censitarios, municipalities, micro/meso regions | Shapefile/GeoJSON download | Free | Updated per census |
| **SREI / ARISP (SP)** | Electronic matricula, averbacao, property records | API (ARISP in SP operational; ONR expanding) | Per-query fees (R$30--R$80 per matricula) | Real-time |
| **ONR (Operador Nacional)** | National digital cartorio access (expanding) | API (in rollout) | Per-query fees | Rolling deployment 2025--2026 |
| **GeoSampa (SP)** | Zoning, land use, infrastructure, IPTU data | REST API + WMS/WFS | Free | Updated periodically |
| **BHMap (BH)** | Zoning, land use, permits, IPTU | Web portal, some API | Free | Updated periodically |
| **Prefeitura portals (other cities)** | Zoning (Plano Diretor), building permits, IPTU | Varies widely -- PDF, web, limited API | Free | Varies |
| **CAIXA auction catalog** | Leilao properties (extrajudicial, alienacao fiduciaria) | Web portal, structured HTML | Free | Updated per auction batch |
| **BB (Banco do Brasil) auctions** | Leilao properties | Web portal | Free | Updated per auction batch |
| **EMGEA auction catalog** | Government NPL property portfolio | Web portal | Free | Periodic |
| **Judicial auction portals** | Leilao judicial properties (TJ portals per state) | Web portal per state (TJ-SP, TJ-RJ, TJ-MG, etc.) | Free | Per auction batch |
| **CAIXA Habitacao / SIOPI** | MCMV program rules, financing rates, subsidy tables | Portal + occasional API | Free | Per program update |
| **CVM dados abertos** | FII data, CRI issuances, real estate securities | Public API | Free | Monthly/quarterly |
| **Receita Federal (e-CAC)** | CNPJ data, tax filings | Portal (authenticated) | Free | Per filing |

### Commercial Data Providers

| Provider | Data Available | Pricing Model | Integration |
|----------|---------------|--------------|-------------|
| **FipeZAP (ZAP+/VivaReal)** | Price index, listing data, rental data | Annual subscription R$20K--R$80K | REST API |
| **DataZAP (OLX B2B)** | Market studies, demand data, listing analytics | Annual subscription R$50K--R$200K | API + reports |
| **Brain Inteligencia Estrategica** | Market studies, demand curves, viability analysis | Per-study R$30K--R$150K | Reports (manual) |
| **Hiperdados** | Property data, market intelligence | Annual subscription R$30K--R$100K | API + dashboard |

### Client Internal Data

Typical internal data sources we need access to during engagements:

- **NF-e (Notas Fiscais Eletronicas)**: Sales and service transaction data for SPE accounting
- **Bank statements**: Per-SPE account statements for patrimonio de afetacao reconciliation
- **Sales contracts**: Compra e venda, promessa, distrato records from CRM/legal
- **CRM pipeline data**: Leads, visits, proposals, conversions from Vista/Hypnobox/CV
- **Construction cost data**: Orcamento, medicao, cronograma from Sienge/UAU
- **Land acquisition documents**: Matriculas, escrituras, due diligence files
- **SPE financial statements**: Balancetes, DRE, fluxo de caixa per entity
- **Investor communications**: Reports, distributions, correspondence

## Integration Patterns

### Pattern 1: Sienge/UAU ERP Integration

**Source:** Sienge (Softplan) or UAU (TOTVS) ERP
**Method:** REST API (Sienge Platform API; TOTVS REST API)
**Challenges:** SPE consolidation not natively supported across entities; financial data access requires proper credential management; API rate limits on historical data extraction
**Solution:** Use ERP API for real-time project/financial data; batch extract historical data for analytics; build SPE consolidation layer on top of per-entity ERP data

### Pattern 2: ITBI Data Aggregation (Per Municipality)

**Source:** Municipal ITBI databases (5,570 municipalities, each different)
**Method:** Web scraping (most cities), REST API (SP via GeoSampa, BH via BHMap, Curitiba), FOIA bulk requests
**Challenges:** No national standard; each municipality has different portal, format, and access rules; data quality varies; geocoding required for cross-city analysis
**Solution:** Build municipality-specific adapters with a common output schema; implement geocoding pipeline (Google Maps / HERE); maintain adapter registry per city; prioritize top 20 cities by client demand

### Pattern 3: SREI / Cartorio Digital Integration

**Source:** ARISP (SP), ONR (national), individual cartorio systems
**Method:** API (ARISP operational; ONR in rollout); fallback to manual request + OCR
**Challenges:** SREI rollout is gradual; per-query costs (R$30--R$80); not all cartorios digitized; OCR quality on older matriculas varies
**Solution:** ARISP API for SP properties; ONR API as it becomes available; OCR + LLM pipeline for non-digital cartorios; cache matricula data to minimize repeated queries

### Pattern 4: FipeZAP Price Index Integration

**Source:** FipeZAP API (ZAP+/VivaReal data)
**Method:** REST API (subscription required)
**Challenges:** Index available at city/neighborhood level, not property-level; listing data ≠ transaction data; requires FipeZAP subscription
**Solution:** Use FipeZAP as one input to AVM alongside ITBI transaction data; calibrate listing-to-transaction discount factor per market; monthly retraining of AVM model

### Pattern 5: Auction Catalog Aggregation

**Source:** CAIXA, BB, EMGEA catalogs; TJ judicial auction portals (per state)
**Method:** Web scraping of structured HTML/PDF
**Challenges:** Each source has different format; judicial portals vary by state; edital PDFs require LLM parsing; catalog updates are batch (not real-time)
**Solution:** Source-specific scrapers with common output schema; LLM-based edital parser for unstructured content; daily monitoring for catalog updates; deduplication across sources

## Recommended Tech Stack

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| **Cloud Platform** | Azure (primary) or AWS | Azure has strong enterprise presence in Brazil; Sienge partnership |
| **Data Platform** | Databricks or Azure Synapse | Handles diverse data sources (ITBI scraping, API data, documents); ML capabilities |
| **Data Ingestion** | Azure Data Factory + custom scrapers | ADF for API-based sources; Python scrapers for ITBI portals and auction catalogs |
| **Document Intelligence** | Azure OpenAI (GPT-4) + Azure AI Document Intelligence | LLM for edital parsing, matricula analysis, contract review |
| **Geospatial** | PostGIS + Kepler.gl / Deck.gl | Property mapping, zoning visualization, setores censitarios analysis |
| **Visualization** | Power BI | Strong mid-market adoption in Brazil; integrates with Azure ecosystem |
| **ML/AI** | Databricks ML or Azure ML | AVM models (hedonic regression, gradient boosting), lead scoring, demand forecasting |
| **Storage** | Azure Data Lake Storage Gen2 | Scalable storage for ITBI transaction history, edital PDFs, matricula documents |
| **API Layer** | Azure API Management or FastAPI | Expose AVM, land scoring, and pipeline data to client systems |
| **OCR** | Azure AI Document Intelligence + Tesseract (fallback) | Matricula digitization, older edital scanning |

## Key Technical Challenges

1. **ITBI data heterogeneity**: Each of Brazil's 5,570 municipalities has a different ITBI system. No national standard exists. Building and maintaining municipality-specific adapters is the core technical moat.

2. **SREI maturity**: Lei 14.382/2022 mandates digital cartorios, but rollout is gradual. SP (ARISP) is ahead; other states lag. Solutions must handle both digital (API) and analog (OCR + LLM) cartorio access.

3. **Document quality**: Older matriculas and editais may be scanned PDFs with poor quality. OCR + LLM pipeline must handle degraded inputs with confidence scoring.

4. **Patrimonio de afetacao complexity**: Each SPE has independent financial obligations. Cross-SPE cash flow optimization while maintaining legal segregation requires careful data modeling.

5. **LGPD compliance for property data**: Aggregating ITBI, buyer, and transaction data at scale requires DPIA, consent management, and anonymization pipelines. Individual-level data cannot be exposed in dashboards.

6. **Geocoding accuracy**: Brazilian addresses are inconsistent (street name variations, missing CEP, informal neighborhoods). Geocoding pipeline must handle fuzzy matching and manual correction queues.

7. **Market data lag**: ITBI transactions reflect 30--90 day old data. FipeZAP indices are monthly. AVM models must account for data recency and adjust confidence intervals accordingly.

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
