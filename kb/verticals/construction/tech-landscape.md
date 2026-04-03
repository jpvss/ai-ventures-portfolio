---
title: "Construction — Technology Landscape"
type: tech-landscape
vertical: construction
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [construction, technology, systems, apis, data-sources, SINAPI, PNCP, BIM]
---

# Construction — Technology Landscape

## Common Client Systems

| System Type | Common Products | Integration Method | Data Format |
|-------------|----------------|-------------------|-------------|
| Construction ERP | Sienge (dominant), TOTVS Protheus/RM, UAU (Globaltec) | REST API (Sienge), ODBC/SQL (TOTVS), file export | Proprietary schemas, CSV |
| BIM / CAD | Autodesk Revit, Archicad, SketchUp, AutoCAD | IFC export, Revit API, file-based | IFC (open standard), RVT (proprietary) |
| BIM Collaboration | Autodoc, BIM 360, Trimble Connect | REST API, file sync | Various |
| Project Scheduling | MS Project, Primavera P6, basic spreadsheets | MPP export, XML, ODBC | MPP, XML, CSV |
| Financial / Accounting | TOTVS, SAP (large firms), Conta Azul (small) | REST API, flat files, ODBC | Various |
| Safety Management | Construpoint, paper-based, basic spreadsheets | API (Construpoint), manual entry | PDF, spreadsheets |
| Condominium Software | Superlogica, Group Software, Townsq | REST API (Superlogica), file export | JSON, CSV, OFX (bank) |
| Document Management | SharePoint, Google Drive, local file servers | File API, manual | PDF, images, Office docs |

## Data Sources

### Public / Government Data

| Source | Data Available | Access Method | Cost | Freshness |
|--------|---------------|--------------|------|-----------|
| **SINAPI** (Caixa Economica Federal) | 100K+ construction cost compositions — labor, materials, equipment by state | Caixa website download (structured CSV/XLS) | Free | Monthly |
| **CUB** (Sinduscon, per state) | Monthly cost per m2 by construction type (R1, R8, R16, CSL, CAL, GI) and state | Sinduscon websites (varies by state) | Free | Monthly |
| **SICRO** (DNIT) | Infrastructure cost compositions — roads, bridges, drainage, earthwork | DNIT website download | Free | Periodic |
| **PNCP** (Portal Nacional de Contratacoes Publicas) | All public procurement: editais, contracts, outcomes from 5,570 municipalities | REST API | Free | Real-time |
| **Diarios Oficiais** (Federal, State, Municipal) | Official publications including licitacao notices, contracts, administrative acts | Varies: official websites, aggregators (Imprensa Nacional, state DOEs) | Free/paid | Daily |
| **Receita Federal CNPJ** | Company registration, CNAE codes, partner structure, legal status | API (limited), bulk download | Free | Regular |
| **CEIS/CNEP** | Sanctioned/debarred companies (impedidos de licitar) | REST API (Portal da Transparencia) | Free | Real-time |
| **IBGE** | Construction industry statistics, demographic data, economic indicators | SIDRA API | Free | Various |
| **RAIS/CAGED** (MTE) | Formal employment data by sector, company, and municipality | Bulk download, limited API | Free | Monthly |
| **ComprasNet** (legacy) | Federal procurement data (being migrated to PNCP) | REST API | Free | Real-time |

### Commercial Data Providers

| Provider | Data Available | Pricing Model | Integration |
|----------|---------------|--------------|-------------|
| **SINAPI Plus** (private enrichment) | Enhanced SINAPI with productivity coefficients and regional adjustments | Subscription | Data files |
| **TCPO (PINI)** | Construction cost and productivity tables — alternative to SINAPI | Annual subscription (~R$2-5K) | PDF/digital, limited structured data |
| **Serasa Experian** | Credit scores, financial risk for subcontractors and partners | Per-query API pricing | REST API |
| **Weather APIs** | Precipitation, temperature, wind — affects construction scheduling | Varies (some free tiers) | REST API |
| **Material price indices** | Steel (IBS), cement (SNIC), aggregates — commodity pricing | Industry association publications | Web scraping, some APIs |
| **Licitacao aggregators** | Pre-filtered public procurement data (Licitacao.net, etc.) | Subscription (R$200-R$2K/month) | Web portal, some APIs |

### Client Internal Data

Typical internal data sources we need access to during engagements:

- **ERP data** (Sienge/TOTVS): Purchase orders, invoices, cost center allocations, project budgets
- **Spreadsheet-based cost control**: Project-specific Excel files with budget vs. actual tracking (most common in mid-market)
- **BIM models**: Revit/IFC files with 3D geometry, element properties, quantity data
- **Project schedules**: MS Project files or spreadsheet-based Gantt charts
- **Bank feeds**: OFX files or API feeds from project bank accounts
- **Safety records**: Inspection reports, incident logs, training records (often paper-based)
- **Permit documentation**: Building permits (alvaras), environmental licenses, CREA ARTs
- **Subcontractor contracts**: Scope, pricing, payment schedules, performance data

## Integration Patterns

### Pattern 1: SINAPI Data Integration

**Source:** Caixa Economica Federal (sinapi.caixa.gov.br)
**Method:** Monthly download of structured CSV/XLS files
**Challenges:** Format changes between months, state-specific datasets (27 UFs), composition code updates, historical series discontinuities
**Solution:** Automated monthly pipeline: download -> schema validation -> delta detection (new/changed/removed compositions) -> database update -> notification to dependent systems

### Pattern 2: PNCP / Procurement Monitoring

**Source:** PNCP (pncp.gov.br)
**Method:** REST API with pagination
**Challenges:** High volume (thousands of publications daily), inconsistent data quality across municipalities, need for NLP classification to filter construction-relevant editais
**Solution:** Event-driven pipeline: API polling (5-minute intervals) -> NLP classification (construction segment, value, region) -> qualification matching -> opportunity scoring -> daily digest generation

### Pattern 3: Diarios Oficiais Scraping

**Source:** Federal (Imprensa Nacional), 27 state DOEs, ~1,000+ municipal DOs
**Method:** Web scraping (most), some APIs (Imprensa Nacional)
**Challenges:** Extreme heterogeneity — each publication has different format, structure, and access method; anti-scraping measures on some sites; OCR required for scanned publications
**Solution:** Priority-based coverage: start with PNCP (structured) + client's operating states -> expand to additional states/municipalities based on opportunity density -> OCR pipeline for scanned publications

### Pattern 4: Sienge ERP Integration

**Source:** Sienge (Softplan) — dominant construction ERP
**Method:** Sienge API (REST) or database connector
**Challenges:** API rate limits, schema varies by client configuration, historical data extraction can be slow
**Solution:** Real-time sync for active project data (API-based) + batch extraction for historical data (database connector) + change data capture for ongoing updates

### Pattern 5: BIM / IFC Data Extraction

**Source:** Revit models exported as IFC (Industry Foundation Classes)
**Method:** IfcOpenShell (Python library) for parsing IFC files
**Challenges:** IFC schema complexity (hundreds of entity types), inconsistent modeling practices across firms, large file sizes (100MB-1GB+), mapping BIM elements to SINAPI/SICRO codes
**Solution:** IFC parser with configurable element extraction rules -> quantity aggregation -> ML-based SINAPI code mapping -> output to cost spreadsheet/ERP format

### Pattern 6: Bank Feed Integration (Condominios)

**Source:** Multiple banks (Itau, Bradesco, BB, Caixa, Santander)
**Method:** OFX file import or bank API (where available)
**Challenges:** Multiple accounts per condominio, different banks with different formats, reconciliation with boleto issuance data
**Solution:** Multi-bank ingestion layer -> transaction normalization -> automated boleto matching -> exception queue for unmatched transactions -> reconciliation dashboard

## Key Ecosystem Players (Technology)

| Player | Role | Relevance |
|--------|------|-----------|
| **Sienge (Softplan)** | Dominant construction ERP | Most common system in mid-market; primary integration target; complement not competitor |
| **Caixa Economica Federal** | SINAPI publisher, MCMV funding | Source of mandatory cost references; SINAPI data is core to our cost intelligence |
| **DNIT** | SICRO publisher, infrastructure procurement | Source of infrastructure cost references; major procurer of public works |
| **Sinduscon** (state chapters) | CUB publisher, industry association | Monthly CUB data is essential for cost indexation and market benchmarking |
| **Autodesk** | BIM tools (Revit, BIM 360) | Dominant BIM platform; our IFC parser must handle Revit-exported files |
| **Autodoc** | Brazilian BIM/document management | Growing platform; potential integration partner for BIM collaboration data |
| **Construpoint** | Digital field management | Potential integration for safety data; partial overlap with our Compliance Tracker |
| **Superlogica** | Condominium management software | Dominant in condominios; integration target for our Condominium Platform |
| **TOTVS** | Generic ERP (Protheus/RM) | Second most common ERP in mid-market construction; integration target |
| **PNCP** | National procurement portal | Single most important external data source for our Public Works Radar |

## Recommended Tech Stack

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| Data Ingestion | SINAPI/CUB parsers (Python) + PNCP API connector + Diarios scrapers (Scrapy) + Sienge API connector | Multi-source construction data integration |
| Storage | PostgreSQL (operational) + S3/Azure Blob (BIM files, documents) + TimescaleDB (time-series cost data) | Handle structured cost data, large BIM files, and time-series indices |
| Processing | Python ML pipeline + LLM (Claude API) for edital/norm analysis + IfcOpenShell for BIM parsing | Cost analysis, NLP, BIM data extraction |
| Analytics | Metabase (dashboards) + custom project dashboards (React) | Cost monitoring, opportunity tracking, compliance status |
| Alerting | WhatsApp Business API + email + SMS | Real-time notifications for variance alerts, licitacao opportunities, permit expirations |
| API Layer | FastAPI (Python) for ERP integration + webhook-based event streaming | Connect to Sienge, TOTVS, and client systems |
| Computer Vision | YOLO/custom model for PPE detection from site photos | NR-18 compliance automation |
| Security | LGPD compliance for employee/resident data, role-based access per project, encrypted storage | Regulatory compliance + multi-project data isolation |
| Infrastructure | AWS or Azure (Brazil South region) | Low-latency access to Brazilian data sources; regional compliance |

## Key Technical Challenges

1. **SINAPI data complexity**: 100K+ compositions across 27 states, with monthly updates and periodic rebases. Mapping client budget items to correct SINAPI codes requires NLP + domain expertise. Solution: ML classification model trained on historical budget-to-SINAPI mappings, with human-in-loop validation.

2. **Diarios Oficiais heterogeneity**: 5,570+ municipalities with different publication formats, many still publishing scanned PDFs. Solution: priority-based coverage starting with PNCP (structured) and major states, expanding coverage based on client needs; OCR pipeline for scanned publications.

3. **BIM model variability**: IFC files from different Revit versions, different modeling standards, and different levels of detail. Solution: configurable IFC parser with fallback rules; start with standardized extraction templates and adapt per client.

4. **Mid-market infrastructure constraints**: Many clients lack IT teams, run on basic shared hosting, or have no cloud infrastructure. Solution: deploy as managed SaaS wherever possible; minimize on-premise requirements; provide white-glove onboarding.

5. **Spreadsheet-to-structured data migration**: Most valuable client data lives in hundreds of Excel files with inconsistent formats. Solution: data extraction pipeline with configurable Excel parsers; initial manual mapping with progressive automation.

6. **Real-time cost data from disconnected sources**: Sienge, spreadsheets, bank feeds, and purchase orders exist in different systems with different update frequencies. Solution: CDC (change data capture) where possible, scheduled sync where not; reconciliation engine to handle timing discrepancies.

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
