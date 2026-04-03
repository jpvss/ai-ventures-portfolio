---
title: "GovTech — Technology Landscape"
type: tech-landscape
vertical: govtech
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [govtech, technology, systems, apis, data-sources, PNCP, open-data]
---

# GovTech — Technology Landscape

## Data Sources

### Public APIs and Open Data

| Source | Data Available | Access Method | Cost | Freshness |
|--------|---------------|--------------|------|-----------|
| **PNCP API** (Portal Nacional de Contratacoes Publicas) | Editais, contracts, atas de registro de preco, supplier data, procurement results | REST API (api.pncp.gov.br), JSON responses, paginated | Free | Real-time (as entities publish) |
| **Portal da Transparencia** (CGU) | Federal budget execution, receitas, despesas, servidores, convenios, CEAF, cartoes corporativos | REST API (api.portaltransparencia.gov.br), JSON | Free | Daily/monthly updates |
| **API Dados Abertos da Camara** | Deputies, expenses (CEAP), propositions, votings, committees | REST API (dadosabertos.camara.leg.br/api/v2), JSON, paginated | Free | Daily updates |
| **API Dados Abertos do Senado** | Senators, expenses, propositions, votings | REST API (legis.senado.leg.br/dadosabertos), XML/JSON | Free | Daily updates |
| **Receita Federal CNPJ** (Dados Abertos) | Company registry: CNPJ, razao social, CNAE, QSA (ownership), situacao cadastral | Bulk CSV download (dados.gov.br), updated monthly; third-party APIs (ReceitaWS, BrasilAPI) | Free (bulk) / R$50--500/mo (API) | Monthly (bulk) |
| **CEIS** (Cadastro Nacional de Empresas Inidôneas e Suspensas) | Sanctioned companies barred from government contracting | REST API via Portal da Transparencia | Free | Updated as sanctions change |
| **CNEP** (Cadastro Nacional de Empresas Punidas) | Companies punished under Lei 12.846/2013 (Anti-Corruption Law) | REST API via Portal da Transparencia | Free | Updated as punishments applied |
| **CEPIM** (Cadastro de Entidades Privadas Sem Fins Lucrativos Impedidas) | NGOs barred from receiving government transfers | REST API via Portal da Transparencia | Free | Updated as restrictions change |
| **CADIN** (Cadastro Informativo de Creditos nao Quitados) | Debtors to the federal government | Restricted access (government entities) | Free (gov) | Real-time |
| **SICAF** (Sistema de Cadastramento Unificado de Fornecedores) | Supplier qualifications, certifications, financial status | Web portal (ComprasNet/PNCP ecosystem) | Free | Updated by suppliers |
| **Querido Diario (OKBR)** | Parsed Diarios Oficiais from 4,000+ municipalities -- procurement notices, appointments, regulatory changes | REST API (queridodiario.ok.org.br/api), full-text search | Free (open source) | Daily scraping |
| **dados.gov.br** | 10,000+ federal government datasets across all areas | Catalog API + direct dataset download (CSV, JSON, API) | Free | Varies by dataset |
| **SIAFI** (Sistema Integrado de Administracao Financeira) | Federal financial execution, budget, payments | Restricted access (federal entities); partial via Portal da Transparencia API | Free (gov) | Real-time |
| **+Brasil (SICONV)** | Federal transfers -- convenios, contratos de repasse, termos de fomento | Web portal + data exports (plataformamaisbrasil.gov.br) | Free | Updated as transfers processed |
| **IBGE APIs** | Geospatial, demographic, economic data by municipality | REST API (servicodados.ibge.gov.br/api) | Free | Census/annual |

### State-Level Procurement Portals

| Portal | State | Access Method | Notes |
|--------|-------|--------------|-------|
| **BEC-SP** (Bolsa Eletronica de Compras) | Sao Paulo | Web scraping, partial API | Largest state procurement volume |
| **CELIC** | Rio Grande do Sul | Web scraping | Centralized state procurement |
| **SIAD** | Minas Gerais | Web scraping | State procurement + environmental cross-reference |
| **ComprasNet Estadual** | Various | Web scraping | Several states run their own ComprasNet instances |
| **Licitacoes-e (Banco do Brasil)** | Multi-state | Web portal, partial API | Electronic auctions for various government entities |

### TCE Digital Systems

| System | TCE(s) | Function | Integration |
|--------|--------|----------|-------------|
| **e-Sfinge** | TCE-SC | Electronic accountability and audit | Data export/API |
| **Sagres** | TCE-PB | Public accounts audit system | Data export |
| **FIPLAN** | TCE-BA | Financial planning and execution | Data export |
| **AUDESP** | TCE-SP | Electronic data collection from municipalities | Data export/API |
| **SIGA** | Various TCEs | Audit management systems | Varies |

## Common Government Systems

| System | Function | Adoption | Integration Method |
|--------|----------|----------|-------------------|
| **SEI** (Sistema Eletronico de Informacoes) | Digital process management | 150+ federal agencies, expanding to states/municipalities | REST API (sei-api), database access |
| **ComprasNet** (legacy) | Federal procurement portal | Federal entities (being replaced by PNCP) | Web scraping, data exports |
| **PNCP** | Centralized procurement portal (Lei 14.133) | Growing -- all levels of government | REST API |
| **e-SIC / Fala.BR** | Citizen information requests (LAI) | All federal entities | Web portal, data exports |
| **SICONV / +Brasil** | Federal transfer management | Federal + recipient entities | Web portal, data exports |
| **SICAF** | Supplier qualification registry | Federal procurement | Web portal (integrated with PNCP) |
| **Betha / Fly / IPM** | Municipal ERP and procurement | Thousands of municipalities | SQL database access, file exports |
| **TOTVS Gestao Publica** | Government ERP | State and municipal entities | REST API, database access |

## Integration Patterns

### Pattern 1: PNCP API Integration

**Source:** PNCP (api.pncp.gov.br)
**Method:** REST API with JSON responses; authentication via API key; paginated results
**Challenges:** API rate limiting; incomplete data for entities still transitioning from ComprasNet; schema changes as platform evolves; some fields optional and inconsistently populated
**Solution:** Implement resilient ingestion with retry logic, incremental extraction using date filters, data quality validation layer, and schema versioning. Cache responses locally; run daily differential updates.

### Pattern 2: Multi-Portal Procurement Aggregation

**Source:** PNCP + ComprasNet + BEC-SP + CELIC-RS + Licitacoes-e + Diarios Oficiais
**Method:** API where available; web scraping with Playwright/Scrapy for portals without APIs; Querido Diario API for Diarios Oficiais
**Challenges:** Each portal has different data models, HTML structures, and update frequencies. Scraping is fragile to UI changes. Deduplication across sources is non-trivial.
**Solution:** Source-specific adapters with standardized output schema. Deduplication using edital number + entity CNPJ + publication date. Monitoring for scraping failures with automatic alerts. Querido Diario API for structured Diario Oficial data.

### Pattern 3: CNPJ Intelligence Pipeline

**Source:** Receita Federal bulk CNPJ data + CEIS/CNEP/CEPIM APIs + QSA ownership data
**Method:** Monthly bulk CNPJ download from dados.gov.br (40GB+ compressed); real-time API calls to CEIS/CNEP/CEPIM; graph database for ownership networks
**Challenges:** Bulk data is massive and requires ETL pipeline; ownership chains can be deep (nested holding companies); PF (pessoa fisica) data restricted by LGPD
**Solution:** PostgreSQL for CNPJ base data; Neo4j or NetworkX for ownership graph analysis; daily incremental updates from sanction databases; LGPD-compliant approach using only public QSA data (PJ owners, not PF)

### Pattern 4: Government Financial Data Integration

**Source:** Portal da Transparencia API + SIAFI (indirect) + +Brasil
**Method:** REST API calls with pagination; scheduled daily/monthly pulls
**Challenges:** Large data volumes (millions of payment records); API rate limiting; data freshness varies by endpoint
**Solution:** Incremental extraction using date parameters; local data warehouse for historical analysis; batch processing for large historical loads; real-time monitoring for daily updates

### Pattern 5: Diario Oficial Processing (via Querido Diario)

**Source:** Querido Diario API (OKBR)
**Method:** REST API with full-text search; returns structured gazette data from 4,000+ municipalities
**Challenges:** Not all municipalities covered; OCR quality varies; some PDFs are image-only
**Solution:** Querido Diario for covered municipalities; custom scraping + OCR pipeline (Tesseract/cloud OCR) for uncovered municipalities; LLM for entity/event extraction from raw text

## Recommended Tech Stack

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| **Cloud Platform** | AWS (primary) or GCP | Broad API support; cost-effective for data-heavy workloads; Lambda for serverless scraping |
| **Data Platform** | PostgreSQL (Supabase) + DuckDB for analytics | PostgreSQL for transactional data and full-text search; DuckDB for analytical queries on large datasets |
| **Data Ingestion** | Python (Airflow/Prefect) | Orchestrated pipelines for multi-source ingestion; custom adapters per data source |
| **Web Scraping** | Playwright + Scrapy | Playwright for JavaScript-rendered portals; Scrapy for static HTML; headless browser for complex interactions |
| **Graph Database** | Neo4j or NetworkX | CNPJ ownership network analysis; related-party detection; supplier relationship mapping |
| **LLM Processing** | Claude API / GPT-4 | Edital analysis, document extraction, audit report generation, natural language queries |
| **ML/Analytics** | scikit-learn + XGBoost | Anomaly detection, price prediction, opportunity scoring; lightweight models for fast iteration |
| **Visualization** | Next.js + Tremor (custom) or Streamlit (internal) | Next.js for public-facing dashboards; Streamlit for internal analytics and prototyping |
| **Search** | Elasticsearch or Typesense | Full-text search across editais, contracts, Diarios Oficiais; faceted search by entity, date, category |
| **Storage** | S3 + PostgreSQL | S3 for raw documents (PDFs, scraped HTML); PostgreSQL for structured extracted data |
| **API Layer** | FastAPI | Expose procurement intelligence as API for client integration; webhook support for alerts |
| **Notifications** | WhatsApp Business API + email (SendGrid) | Real-time procurement alerts; WhatsApp for high-engagement time-sensitive notifications |

## Key Technical Challenges

1. **Data fragmentation**: No single source covers all procurement. PNCP adoption is growing but not universal. State portals, municipal Diarios Oficiais, and legacy ComprasNet remain necessary for comprehensive coverage.

2. **Scraping fragility**: State/municipal portals change their HTML structure without notice. Scraping pipelines require continuous monitoring and maintenance. Querido Diario reduces this burden for Diarios Oficiais but doesn't cover all municipalities.

3. **CNPJ data scale**: Receita Federal bulk CNPJ data is 40GB+ compressed with 50M+ records. Ownership graph analysis on this scale requires optimized data engineering. Monthly updates require efficient incremental processing.

4. **LLM accuracy for legal Portuguese**: Edital analysis requires understanding of Brazilian legal language, procurement terminology, and regulatory context. LLM models need careful prompting and validation to achieve >90% extraction accuracy.

5. **LGPD compliance**: Processing CNPJ data is generally safe (PJ data), but ownership analysis can expose PF (pessoa fisica) data. LGPD compliance requires careful handling of any personal data encountered in procurement records.

6. **Rate limiting and API stability**: Government APIs (PNCP, Portal da Transparencia) have rate limits and occasional downtime. Resilient ingestion with retry logic, caching, and graceful degradation is essential.

7. **Deduplication across sources**: The same procurement notice may appear on PNCP, a state portal, and a Diario Oficial with slightly different formatting. Robust deduplication using procurement identifiers (edital number + entity CNPJ) is critical.

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
