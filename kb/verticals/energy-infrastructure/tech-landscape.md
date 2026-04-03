---
title: "Energy & Infrastructure — Technology Landscape"
type: tech-landscape
vertical: energy-infrastructure
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [energy-infrastructure, technology, systems, apis, data-sources, SolarZ, Growatt, ANEEL, CCEE]
---

# Energy & Infrastructure — Technology Landscape

## Common Client Systems

| System Type | Common Products | Market Position | Integration Method | Data Format |
|-------------|----------------|-----------------|-------------------|-------------|
| **Monitoring** | SolarZ | Market leader, inverter-agnostic, 100K+ plants | REST API | JSON, time-series |
| **Monitoring** | Growatt Cloud | Growatt inverters, free with hardware | REST API | JSON |
| **Monitoring** | Huawei FusionSolar | Huawei inverters, enterprise-grade | REST API (partner credentials required) | JSON |
| **Monitoring** | Fronius Solar.web | Fronius inverters | REST API | JSON |
| **Billing** | Excel / Google Sheets | 80%+ of gestoras | CSV export, manual | Spreadsheets |
| **Billing** | Eleva Energia | Emerging GD operations platform | API (limited) | Proprietary |
| **CRM/Sales** | Genial Solar | Integradores | Web platform | Proprietary |
| **CRM/Sales** | Pipedrive / HubSpot | Generic, used by some integradores | REST API | JSON |
| **Financial** | Omie | Small/mid-market accounting | REST API | JSON |
| **Financial** | ContaAzul | Small business accounting | REST API | JSON |
| **Financial** | TOTVS Protheus | Larger comercializadoras | REST API | JSON/SQL |

## Data Sources

### Public/Government APIs and Systems

| Source | Data Available | Access Method | Cost | Freshness |
|--------|---------------|--------------|------|-----------|
| **ANEEL SIGA** (Sistema de Informacoes de Geracao) | GD plant registry -- capacity, location, distribuidora, connection date, technology | Web portal + downloadable datasets | Free | Monthly updates |
| **ANEEL BIG** (Banco de Informacoes de Geracao) | Generation capacity, plant status, ownership | Web portal + API | Free | Updated periodically |
| **CCEE InfoMercado** | Mercado Livre prices (PLD), settlement data, consumption/generation volumes | Web portal + downloadable reports | Free (basic) / Subscription (detailed) | Daily PLD, monthly reports |
| **CCEE SCDE** (Sistema de Coleta de Dados de Energia) | Metering data for settlement | Authenticated API (agents only) | Included for registered agents | Real-time |
| **CCEE CLIQ** | Energy trading platform, contract management | Authenticated web platform | Included for registered agents | Real-time |
| **INMET** (Instituto Nacional de Meteorologia) | Irradiation, temperature, humidity, wind speed from weather stations | Public API (BDMEP), CSV downloads | Free | Hourly updates |
| **NSRDB** (National Solar Radiation Database) | Historical solar resource data (GHI, DNI, DHI), high-resolution | API (NREL) | Free | Historical dataset |
| **EPE Atlas Solar** | Solar resource mapping for Brazil | Web portal, downloadable GIS data | Free | Periodically updated |
| **Receita Federal CNPJ** | Company data -- razao social, CNAE code, porte, address, situacao cadastral | Public consultation + unofficial APIs | Free (public) / Rate-limited | Updated periodically |
| **Google Places API** | Business establishments -- name, type, location, reviews, hours | REST API | Pay-per-use (~$17/1000 requests) | Real-time |
| **Distribuidora portals** (CEMIG, Enel, CPFL, Energisa, Equatorial, Neoenergia) | UC compensation reports, faturas, credit balances, connection data | Web portals (login-authenticated), some APIs emerging | Free (for registered consumers) | Monthly billing cycle |

### Commercial Data Providers

| Provider | Data Available | Pricing Model | Integration |
|----------|---------------|--------------|-------------|
| **SolarZ API** | Aggregated plant monitoring data, alerts, performance metrics | Included with SolarZ subscription | REST API |
| **Growatt Cloud API** | Inverter-level generation data, status, alerts | Free with Growatt hardware | REST API |
| **Huawei FusionSolar API** | Inverter and plant-level generation, performance data | Free with Huawei hardware (partner credentials) | REST API |
| **Greener** (market data) | Solar market pricing, equipment benchmarks, regional market data | Subscription | Reports, downloadable data |

### Client Internal Data

Typical internal data sources we need access to during engagements:

- **UC portfolio database**: List of all consumer units with CNPJ/CPF, distribuidora, connection date (pre/post Marco Legal), plant assignment, allocation percentage
- **Billing records**: Historical faturas per UC, compensation credits applied, kWh injected/compensated, fio B charges
- **Generation data**: Inverter telemetry (kWh per interval), performance ratios, downtime logs
- **Payment records**: UC-level payment history, default events, collection actions
- **Sales pipeline**: Lead sources, prospect data, proposal history, conversion outcomes
- **Contract data**: CUSD/CCEAR contracts with distribuidoras, tariff structures, term/volume/price
- **Financial data**: Revenue per UC, COGS, operating expenses, cash flow

## Integration Patterns

### Pattern 1: Distribuidora Fatura Integration

**Source:** CEMIG, Enel, CPFL, Energisa, Equatorial, Neoenergia portals
**Method:** Authenticated web scraping (login + navigation), PDF download + OCR parsing, emerging APIs
**Challenges:** Each distribuidora has a different portal UX, fatura format, and data fields; portals require manual login (CAPTCHA, 2FA); fatura PDFs have varying layouts; some distribuidoras offer compensation reports in Excel
**Solution:** Build distribuidora-specific scrapers with headless browser (Playwright/Puppeteer); use LLM-assisted PDF parsing for fatura extraction; normalize to common schema (UC, period, kWh injected, kWh compensated, TUSD, TE, fio B, credit balance); scheduled daily/weekly extraction

### Pattern 2: Multi-Inverter API Integration

**Source:** Growatt Cloud, Huawei FusionSolar, SolarZ, Fronius Solar.web
**Method:** REST APIs with manufacturer-specific authentication (API keys, OAuth)
**Challenges:** Different data models per manufacturer; varying granularity (5-min, 15-min, hourly); API rate limits; Huawei requires partner-level credentials
**Solution:** Build inverter-agnostic abstraction layer; normalize to common time-series schema (timestamp, plant_id, inverter_id, power_kw, energy_kwh, status); store in TimescaleDB for efficient time-series queries; use SolarZ as aggregator when available

### Pattern 3: Irradiation Data Integration

**Source:** INMET weather stations, NSRDB historical data, commercial satellite providers
**Method:** INMET public API (BDMEP endpoint), NSRDB API (NREL), CSV downloads
**Challenges:** INMET station coverage gaps in some regions; data quality issues (missing readings, sensor errors); temporal resolution mismatch with generation data
**Solution:** Use NSRDB for historical baseline (TMY -- Typical Meteorological Year); INMET for real-time adjustments; interpolation for stations without nearby coverage; automated data quality checks

### Pattern 4: Google Places + CNPJ Lead Enrichment

**Source:** Google Places API, Receita Federal CNPJ consultation
**Method:** REST APIs (Google Places, unofficial CNPJ APIs), rate-limited queries
**Challenges:** Google Places API cost at scale; CNPJ API rate limits; matching Google Places results to CNPJ records; estimating energy consumption from CNAE code
**Solution:** Batch processing with caching; CNAE-to-consumption lookup tables (based on ANEEL/EPE benchmarks); geographic filtering to target regions; result storage in PostgreSQL for CRM integration

### Pattern 5: CCEE Market Data Integration

**Source:** CCEE InfoMercado, SCDE, CLIQ
**Method:** Web portal downloads (InfoMercado), authenticated API (SCDE for registered agents), CLIQ platform
**Challenges:** CCEE systems require agent registration; data formats vary (CSV, XML); settlement data is complex (liquidation rules, MRE adjustment)
**Solution:** Scheduled downloads from InfoMercado for PLD data; SCDE integration for metering data (comercializadoras only); parse and store in time-series database; build settlement reconciliation logic

## Recommended Tech Stack

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| **Cloud Platform** | AWS (primary) or GCP | Cost-effective for startups; Lambda for scheduled jobs; S3 for data lake |
| **Primary Database** | PostgreSQL (Supabase or RDS) | Relational data (UCs, contracts, leads); strong ecosystem; Supabase adds auth/realtime |
| **Time-Series Database** | TimescaleDB (PostgreSQL extension) | Generation data, irradiation, PLD prices; efficient time-series queries on PostgreSQL |
| **Data Ingestion** | Python scripts (scheduled via cron/Lambda) | Distribuidora scrapers, inverter API connectors, INMET/CCEE data pulls |
| **PDF Parsing** | Python (pdfplumber, Camelot) + LLM fallback | Fatura PDF extraction; LLM for unstructured/variable formats |
| **Web Scraping** | Playwright (Python) | Distribuidora portal authentication and navigation |
| **Visualization** | Metabase (self-hosted) or custom React dashboards | Metabase for rapid deployment; React for investor-grade custom reports |
| **ML/AI** | Python (scikit-learn, LightGBM, Prophet) | Default prediction, generation forecasting, lead scoring |
| **API Layer** | FastAPI (Python) | REST API for frontend, webhook integrations, CRM connectors |
| **Frontend** | Next.js + Tailwind CSS | Dashboard UIs, investor report portals |
| **Notifications** | WhatsApp Business API, SendGrid | Billing alerts, collection messages, sales notifications |
| **Storage** | AWS S3 | Fatura PDFs, generation data exports, report archives |

## Key Technical Challenges

1. **Distribuidora portal fragility**: Web scrapers break when distribuidoras update their portals. Requires monitoring and rapid adapter updates. Emerging APIs (CEMIG, Enel) may reduce scraping dependency over time.

2. **Fatura format heterogeneity**: Each distribuidora uses different PDF layouts. LLM-assisted parsing improves accuracy but adds latency and cost. Building distribuidora-specific parsers is more reliable for high-volume processing.

3. **Inverter API authentication**: Huawei FusionSolar requires partner-level credentials that can be difficult to obtain. Growatt API documentation is limited. SolarZ provides the best aggregated access but adds a subscription dependency.

4. **Pre/post Marco Legal complexity**: Dual calculation logic (full compensation vs. fio B) with progressive annual percentages creates edge cases. Plants connected near the July 2023 cutoff require careful date verification.

5. **Data quality at the edges**: INMET irradiation data has coverage gaps in some regions. Inverter telemetry has missing readings during connectivity outages. Distribuidora faturas occasionally contain errors. All integration pipelines need automated data quality checks.

6. **LGPD compliance**: UC holder data (CPF/CNPJ, consumption, address) is personal data under LGPD. Systems must implement consent management, data access controls, and retention policies. Prospecting pipelines must handle CNPJ data in compliance with data protection rules.

7. **Scaling across distribuidoras**: Brazil has 53 distribuidoras, each with different portals, formats, and rules. Initial implementations focus on major ones (CEMIG, Enel, CPFL, Energisa), with a framework for adding new distribuidoras incrementally.

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
