---
title: "Automotive — Technology Landscape"
type: tech-landscape
vertical: automotive
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [automotive, technology, systems, apis, data-sources, FIPE, Parallelum, DENATRAN]
---

# Automotive — Technology Landscape

## Common Client Systems

| System Type | Common Products | Integration Method | Data Format |
|-------------|----------------|-------------------|-------------|
| Dealer Management System (DMS) | Dealer Solutions, Linx Automotivo, SysCar, custom-built Excel/Google Sheets | SQL export, CSV, REST API (newer DMS) | Proprietary; many still file-based |
| Financial / Floor Plan | Bank floor plan systems (Santander, Itaú, BV), TOTVS | Web portal, file export | PDF statements, CSV |
| CRM | HubSpot, Pipedrive, RD Station, custom-built | REST API | JSON |
| Marketplace Listing | Webmotors portal, OLX portal, iCarros portal | Web UI (manual), bulk upload (CSV), API (premium accounts) | Varies by marketplace |
| Accounting | TOTVS, ContaAzul, custom | REST API, flat files | Various |
| Vehicle Photo Management | Manual (phone photos), RepoAuto, custom | File system, cloud storage | JPEG/PNG |
| Insurance / Financing Partners | Broker portals, bank APIs | Web portal, manual | PDF, web forms |

## Data Sources

### Public/Government APIs

| Source | Data Available | Access Method | Cost | Freshness |
|--------|---------------|--------------|------|-----------|
| **FIPE / Parallelum API** | Monthly reference prices for all vehicles by make/model/year/fuel | REST API (api.parallelum.com.br) | Free tier (rate limited) / Paid plans | Monthly (1st business day) |
| **DENATRAN/SENATRAN** | National vehicle fleet by municipality, type, age; transfer volumes | Data portal + CSV downloads (dados.gov.br) | Free | Monthly/quarterly |
| **DETRAN (by state)** | Vehicle registration (CRLV), restrictions, débitos, transfer status | Varies by state: API (SP, RJ), web portal (most others) | Free / per-query fees (varies) | Real-time (for queries) |
| **IBGE** | Regional demographic data, economic indicators by municipality | REST API (servicodados.ibge.gov.br) | Free | Census/annual |
| **DENATRAN Recall Database** | Active and historical vehicle recalls by make/model/year | Web portal + data downloads | Free | Real-time |
| **Receita Federal CNPJ** | Dealer registration data, legal status, CNAE codes | API | Free/limited | Updated regularly |

### Commercial Data Providers / Marketplaces

| Provider | Data Available | Pricing Model | Integration |
|----------|---------------|--------------|-------------|
| **Webmotors** (Santander) | Active listings with prices, photos, specs, dealer data; ~500K+ active | Listing fees for dealers; no public data API | Web scraping required; premium dealer accounts have bulk export |
| **OLX Autos** | Active listings with prices, location, seller type; millions of listings | Listing fees; no public data API | Web scraping required |
| **iCarros** (Itaú) | Active listings with financing simulation | Listing fees | Web scraping |
| **Tabela FIPE Online** | Public FIPE lookup interface | Free (web) | Parallelum API is the programmatic equivalent |
| **Molicar / Automotive databases** | Vehicle specifications (engine, transmission, dimensions, optionals) | Subscription | Varies |

### Client Internal Data

Typical internal data sources we need access to during engagements:
- **Inventory data**: Current stock (make/model/year/km/condition/acquisition date/acquisition cost), stored in DMS or spreadsheet
- **Transaction history**: Sale price, sale date, days-on-lot, buyer profile, financing/insurance attachment
- **Acquisition records**: Vehicle source (trade-in, direct buy, auction), acquisition price, evaluator notes
- **Floor plan statements**: Monthly financing costs per vehicle, interest rates, payoff amounts
- **Marketplace listing data**: Current listings across platforms, listing dates, price change history
- **Customer/lead data**: CRM records, inquiry sources, conversion data

## Integration Patterns

### Pattern 1: FIPE/Parallelum API Integration

**Source:** Parallelum API (api.parallelum.com.br)
**Method:** REST API — GET endpoints for brands, models, years, price references
**Challenges:** Rate limiting on free tier (~500 requests/day); occasional downtime; data only updates monthly; no historical API (only current month)
**Solution:** Supabase cache layer with monthly refresh cycle (proven in deixacomigo); local storage of historical FIPE tables for trend analysis; fallback to cached data when API is unavailable
**deixacomigo Reference:** Full implementation exists — TypeScript, Supabase caching, cascading brand > model > year selection

### Pattern 2: Marketplace Scraping (OLX/Webmotors)

**Source:** OLX Autos, Webmotors, iCarros
**Method:** Web scraping (no public APIs available)
**Challenges:** DOM structure changes frequently; anti-bot measures (Cloudflare, CAPTCHAs); volume of data (millions of listings); maintaining up-to-date comparable sets
**Solution:** Playwright/Puppeteer-based scrapers running on AWS Lambda or dedicated EC2; rotating proxies; structured data extraction pipeline; scheduled daily runs for priority makes/models; incremental scraping (new/changed listings only)
**Maintenance:** Scraper maintenance is a retainer item — DOM changes require updates every 4–8 weeks on average

### Pattern 3: DENATRAN/SENATRAN Fleet Data

**Source:** DENATRAN via dados.gov.br (open data portal)
**Method:** CSV/XLSX download (bulk); some datasets available via API
**Challenges:** Large file sizes (national fleet data); varying data quality and format changes between releases; monthly publication lag
**Solution:** ETL pipeline that downloads, validates, and loads DENATRAN data into PostgreSQL; geographic normalization (municipality codes to lat/long); aggregation tables for fast regional demand queries

### Pattern 4: DETRAN State Integration

**Source:** 27 state DETRANs
**Method:** Varies dramatically by state — SP has API; RJ has partial API; most states are web-portal only
**Challenges:** No national standard; each state has different systems, formats, and access policies; some require physical presence or specific credentials
**Solution:** State-specific integration adapters; prioritize SP (largest market), then RJ, MG, PR, RS; for non-API states, use authorized data aggregators (ex: Olho no Carro, Checkauto) that have established connections
**Priority States:** São Paulo (30% of market), Minas Gerais, Rio de Janeiro, Paraná, Rio Grande do Sul — these 5 cover ~65% of used car transactions

### Pattern 5: Vehicle Photo Processing (LLM Vision)

**Source:** Vehicle photos taken by dealer staff (10–20 photos per vehicle)
**Method:** Upload to cloud storage → process via LLM vision API (Claude, GPT-4V)
**Challenges:** Photo quality varies (lighting, angles, resolution); need to detect specific damage types (scratches, dents, rust, tire wear, interior stains); no standardized automotive damage taxonomy
**Solution:** Prompt-engineered LLM vision pipeline: (1) classify photo type (exterior front/rear/side, interior, engine, tires, damage detail); (2) identify and grade damage items; (3) generate structured condition report with severity scores; (4) calculate condition adjustment factor for pricing model
**Cold Start:** Start with rule-based condition scoring from manual input; add LLM vision as enhancement after 500+ labeled photo sets

## Key Ecosystem Players (Technology)

| Player | Role | Relevance |
|--------|------|-----------|
| **Parallelum** | FIPE API provider | Standard programmatic access to FIPE data; used in deixacomigo; will be integrated in every automotive project |
| **Webmotors** (Santander) | Marketplace leader | Primary comparable pricing data source; scraping required |
| **OLX Autos** | Largest classifieds | Broadest listing coverage; essential for pricing intelligence |
| **DENATRAN/SENATRAN** | Fleet registry | National vehicle data; regional demand analysis |
| **Olho no Carro / Checkauto** | Vehicle history aggregators | Consolidate DETRAN, lien, accident, and recall data; potential integration partner |
| **Dealer Solutions / Linx** | DMS providers | Common client systems we integrate with; limited APIs |
| **Creditas / BV** | Vehicle-backed fintechs | Potential clients for collateral valuation; also set market benchmarks |
| **Localiza / Movida** | Fleet disposal operations | Largest sellers; pricing data from their seminovos operations is market-moving |

## Recommended Tech Stack

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| Data Ingestion | FIPE/Parallelum API (TypeScript) + Playwright scrapers (OLX/Webmotors) + DENATRAN ETL (Python) | Multi-source pricing data; proven FIPE integration from deixacomigo |
| Storage | Supabase (PostgreSQL + RLS) + Redis cache | Proven in deixacomigo; RLS for multi-tenant white-label deployments |
| Processing | Python ML pipeline (scikit-learn, XGBoost, LightGBM) + TypeScript business logic (Next.js) | Pricing models in Python; application layer in TypeScript (consistent with deixacomigo) |
| Analytics | Metabase (dealer dashboard) or custom Next.js dashboards (Tremor/Recharts) | Metabase for quick deployment; custom for branded experiences |
| API Layer | Next.js API Routes (application) + standalone Python API (ML model serving) | Consistent with deixacomigo architecture; separate ML serving for performance |
| AI/Vision | Anthropic Claude API (vehicle photo assessment) or OpenAI GPT-4V | LLM vision for condition grading; Claude already integrated in deixacomigo |
| Email/Notifications | Resend (transactional email) + WhatsApp Business API (dealer notifications) | Resend proven in deixacomigo; WhatsApp for dealer-facing alerts (Brazilian market standard) |
| Infrastructure | Vercel (application) + Supabase (database) + AWS Lambda (scrapers) | Consistent with deixacomigo; Lambda for scheduled scraping jobs |

## Key Technical Challenges

1. **Marketplace scraping reliability**: OLX and Webmotors actively block scrapers. DOM changes every 4–8 weeks. Solution: Playwright with rotating residential proxies; structured monitoring for DOM changes; fallback data from cached listings.

2. **FIPE monthly lag**: FIPE publishes once per month, but market prices can shift weekly (e.g., new model launch, exchange rate change, tax policy). Solution: Use FIPE as baseline but weight marketplace real-time data for current pricing; flag when marketplace diverges >5% from FIPE.

3. **State-level DETRAN fragmentation**: 27 different systems with different capabilities. Solution: Start with SP (largest, has API); expand to authorized aggregators (Olho no Carro) for other states; build state-agnostic abstraction layer.

4. **Vehicle condition subjectivity**: Even with photos, condition assessment involves judgment. Solution: Standardized 5-axis scoring framework + LLM vision for consistency; human override for edge cases; calibrate LLM assessments against expert evaluator ground truth.

5. **Data freshness for pricing models**: Marketplace data goes stale quickly; a listing that disappeared might be sold or just delisted. Solution: Track listing lifecycle (new, price changed, removed); weight recent listings more heavily; flag vehicles with insufficient comparables.

6. **Multi-tenant architecture for white-label**: White-label deixacomigo deployments need tenant isolation. Solution: Supabase RLS policies (already in deixacomigo architecture); per-tenant pricing algorithm calibration; shared infrastructure, isolated data.

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
