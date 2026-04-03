---
title: "Auction Market — Technology Landscape"
type: tech-landscape
vertical: auctions
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [auctions, technology, systems, apis, data-sources, scraping, Caixa, FipeZap]
---

# Auction Market — Technology Landscape

## Common Client Systems

The auction vertical has a uniquely fragmented technology landscape with no dominant platform or standard system:

| System Type | Common Products | Integration Method | Data Format |
|-------------|----------------|-------------------|-------------|
| Leiloeiro platforms | 1,000+ individual websites (heterogeneous) | Web scraping (Scrapy/Playwright) | HTML, JavaScript-rendered, PDFs |
| Bank auction portals | Caixa, Santander, Banco do Brasil proprietary platforms | API via Apify, web scraping | Structured JSON (Caixa), HTML |
| TJ judicial systems | 27 state-specific Tribunal de Justica portals | Web scraping (per-state adapters) | HTML, PDF editais |
| White-label SaaS | Sua Plataforma de Leilao (100+ leiloeiro clients) | Potential B2B API | Variable |
| Property valuation | FipeZap, OLX, ZAP, QuintoAndar, VivaReal | Scraping, API (limited), data download | HTML, Excel (FipeZap), JSON |
| Cartorio systems | Cartorio de Registro de Imoveis (per-municipality) | Manual visits, some digitization | PDF matriculas |

## Data Sources

### Public/Government Data

| Source | Data Available | Access Method | Cost | Freshness |
|--------|---------------|--------------|------|-----------|
| **Caixa Economica Federal** | Property listings: evaluationValue, minimumSaleValue, discount, area, matriculaUrl, paymentMethods | Structured API via Apify | Free (Apify compute costs) | Daily updates |
| **Santander** | Property auction listings | API via Apify | Free (Apify compute costs) | Daily updates |
| **TJ databases (27 states)** | Judicial auction listings, edital documents | Web scraping (per-state adapters) | Free (scraping infrastructure costs) | Varies by state |
| **Receita Federal SLE** | Tax data, e-CAC portal | Portal access (authenticated) | Free | As updated |
| **IPTU/Municipal databases** | Property tax status, outstanding debts | Varies by municipality | Free | Varies |

### Commercial Data Providers

| Provider | Data Available | Pricing Model | Integration |
|----------|---------------|--------------|-------------|
| **FipeZap/DataZap** | Price indices for 50+ cities, historical price data | Excel download, potential API | Excel download; some API access for partners |
| **QuintoAndar** | Rental/sale listings, price comparables | Scraping via Apify marketplace | Apify actors available |
| **OLX** | Property listings, price comparables | Scraping via Apify marketplace | Apify actors available |
| **ZAP Imoveis** | Property listings, price comparables | Scraping via Apify marketplace | Apify actors available |
| **VivaReal** | Property listings, price comparables | Scraping via Apify marketplace | Apify actors available |
| **Geoimovel** | AI-powered location/price mapping, proptech data | Commercial API | B2B partnership |
| **Apify marketplace** | Pre-built scrapers for Caixa, Santander, OLX, QuintoAndar, ZAP | Pay-per-use (compute-based) | Cloud-based actors |

### Client Internal Data

Typical internal data sources we need access to during engagements:

- **Deal screening records**: Historical properties evaluated, bids placed, outcomes
- **Valuation spreadsheets**: Manual comparable analyses performed to date
- **Legal analysis files**: Lawyer reviews of editais, matriculas, certidoes
- **Post-arrematacao tracking**: Registration timelines, desocupacao records, renovation costs
- **Client/investor profiles**: Investment criteria, risk tolerance, geographic preferences
- **Financial records**: Investment returns, cost breakdowns, portfolio performance

## Integration Patterns

### Pattern 1: Caixa Economica Federal API (via Apify)

**Source:** Caixa property auction platform
**Method:** Structured API via Apify actors
**Data Fields:** evaluationValue, minimumSaleValue, discount, area, matriculaUrl, paymentMethods
**Challenges:** Rate limiting, data freshness, occasional format changes
**Solution:** Scheduled Apify runs with error handling and retry logic; local caching in Redis

### Pattern 2: Leiloeiro Website Scraping

**Source:** 1,000+ individual leiloeiro websites
**Method:** Web scraping with Playwright/Puppeteer
**Challenges:**
- Heterogeneous HTML formats (no standard schema)
- JavaScript rendering required for many sites
- CAPTCHAs on some platforms
- Session-based authentication
- Anti-scraping measures
- Frequent site redesigns break scrapers
**Solution:** Playwright for JS-heavy sites, rotating proxies, CAPTCHA solving services, per-site adapter architecture with fallback to generic extractors, monitoring and alerting for broken scrapers

### Pattern 3: TJ Portal Scraping (Judicial Auctions)

**Source:** 27 state Tribunal de Justica systems
**Method:** Web scraping with per-state adapters
**Challenges:** Each state has a different system, anti-scraping measures, PDF editais requiring OCR
**Solution:** State-specific scraping modules, PDF download and OCR pipeline, centralized data normalization

### Pattern 4: Real Estate Portal Data (FipeZap, OLX, ZAP, QuintoAndar)

**Source:** Major Brazilian real estate listing platforms
**Method:** Apify marketplace scrapers, FipeZap Excel downloads
**Challenges:** Data standardization across platforms (different property descriptions, price formats, area measurements)
**Solution:** Normalization layer that maps platform-specific fields to unified schema; deduplication based on address/coordinates

### Pattern 5: Edital/Matricula Document Processing

**Source:** PDF editais from leiloeiro sites and TJ systems; matricula documents from cartorios
**Method:** OCR (Azure AI Document Intelligence / Tesseract) + NLP extraction (GPT-4/Claude)
**Challenges:** Variable document quality (scanned vs. digital PDFs), legal terminology, unstructured text, no standard format
**Solution:** Azure AI Document Intelligence for high-quality OCR, Portuguese-trained LLMs for entity extraction and risk identification, structured output with confidence scoring

## Recommended Tech Stack

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| **Web Scraping** | Playwright/Puppeteer | Handles JavaScript-rendered sites, headless browser automation; superior to Scrapy for modern auction sites |
| **Scraping Infrastructure** | Rotating proxies, CAPTCHA solving services | Required to maintain access across 1,000+ sites with anti-scraping measures |
| **Scraping Orchestration** | Scrapy (for simpler sites), Apify (for marketplace actors) | Scrapy for batch crawling simpler sites; Apify for pre-built actors (Caixa, Santander, OLX) |
| **Primary Database** | PostgreSQL | Robust relational storage for structured property data, investor profiles, transaction records |
| **Search Engine** | Elasticsearch | Full-text search across property descriptions, edital text, locations; faceted filtering |
| **Caching** | Redis | High-frequency data access, scraping rate limiting, session management |
| **Message Queue** | Kafka or RabbitMQ | Real-time alert processing, event-driven architecture for new listing notifications |
| **OCR** | Azure AI Document Intelligence or Tesseract | Edital and matricula PDF processing; Azure for higher accuracy, Tesseract for cost control |
| **NLP/LLM** | GPT-4/Claude (Portuguese-trained) | Legal text interpretation, entity extraction from editais and matriculas |
| **ML Framework** | Gradient boosting (XGBoost/LightGBM) + neural nets | AVM model training; gradient boosting for structured features, neural nets for complex patterns |
| **Frontend** | React/Next.js | Modern SPA framework for investor-facing dashboards |
| **Map Visualization** | Mapbox | Geolocation visualization for property maps, cluster views, neighborhood analysis |
| **Notifications** | WhatsApp Business API, email (SendGrid/SES) | Primary alert channels; WhatsApp preferred by Brazilian investors |
| **Geocoding** | Google Maps Geocoding API or Nominatim | Address-to-coordinates conversion for property mapping |

## Key Technical Challenges

### 1. No Unified Property Identifier
Matricula numbers are cartorio-specific, meaning the same property has different identifiers in different systems. There is no national property registry equivalent to a CNPJ for properties.
**Our Solution:** Geocoding-based deduplication using address normalization + coordinates as the de facto unique identifier.

### 2. Heterogeneous Data Formats
1,000+ leiloeiro websites each with different HTML structures, terminology, and data formats.
**Our Solution:** Per-site adapter architecture with generic fallback extractors. Monitoring system detects format changes within 24 hours.

### 3. Anti-Scraping Measures
TJ portals and some leiloeiro sites employ CAPTCHAs, rate limiting, IP blocking, and JavaScript obfuscation.
**Our Solution:** Rotating residential proxies, CAPTCHA solving services, Playwright for full browser emulation, respectful crawling rates.

### 4. PDF Document Processing
Many editais are PDF documents (some scanned, some digital) requiring OCR and NLP extraction.
**Our Solution:** Azure AI Document Intelligence for high-quality OCR with layout understanding. Portuguese-trained LLMs for legal entity extraction. Confidence scoring to flag documents needing human review.

### 5. Data Freshness
Auction listings have time-sensitive deadlines (5-day minimum pre-lance per CNJ Resolucao 236). Stale data means missed opportunities.
**Our Solution:** Daily refresh cadence minimum, with near-real-time scraping for high-priority sources. Redis caching for frequently accessed data. Alert latency target: within 15 minutes of listing.

### 6. LGPD Compliance in Scraping
Scraped data may contain debtor PII (names, addresses, financial information).
**Our Solution:** Data minimization — collect only property and auction data, not debtor personal information. Where debtor data is unavoidable (edital text), apply anonymization and access controls.

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
