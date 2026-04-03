---
title: "Auction Market — Solution Patterns"
type: solution-patterns
vertical: auctions
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [auctions, solutions, technical, patterns, aggregation, AVM, legal-risk, edital-parser]
---

# Auction Market — Solution Patterns

## Reusable Solution Components

### Pattern 1: Data Aggregation

**Problem:** Over 1,000 leiloeiro websites in Brazil with heterogeneous formats, no standardized data, and no centralized database. Professional investors can only screen a fraction of available deals manually.

**Solution Architecture:**
Web scraping cluster (Scrapy/Playwright) -> ETL pipeline -> normalized PostgreSQL + Elasticsearch -> search/filter API -> frontend

**Vertical-Specific Details:**
- Must handle JavaScript-rendered sites, CAPTCHAs, and session-based authentication
- Rotating proxies required due to anti-scraping measures on TJ portals
- Daily refresh cadence for data freshness
- Must normalize heterogeneous data formats from 500+ sources into a unified schema
- Property addresses need geocoding for map visualization

**Cross-Vertical Pattern:** See `kb/patterns/data-integration.md` (data integration as foundation project)

**Estimated Effort:** R$250K-R$400K, 3-4 months

**Expected ROI:** 10x more properties analyzed; foundation for all other auction AI projects

### Pattern 2: Document Intelligence (Edital/Matricula Parsing)

**Problem:** Manual edital analysis costs ~R$2,000 per property for lawyer review. Checking a matricula for encumbrances requires manual cartorio visits.

**Solution Architecture:**
PDF ingestion -> OCR (Azure AI Document Intelligence/Tesseract) -> NLP extraction (GPT-4/Claude) -> structured data -> risk scoring rules engine

**Vertical-Specific Details:**
- Edital parsing extracts: key terms, deadlines, payment conditions, encumbrances, minimum prices
- Matricula OCR extracts: ownership chain, onus, penhoras, hipotecas, pending lawsuits
- Certidao cross-referencing validates extracted data
- Portuguese-trained LLMs required for legal text interpretation
- Output: risk score (0-100), flagged issues, recommended actions

**Cross-Vertical Pattern:** See `kb/patterns/document-intelligence.md` (same pipeline serves editais in auctions, apolices in insurance, environmental licenses in mining)

**Estimated Effort:** R$200K-R$350K, 3-5 months (Legal Risk Scorer); R$80K-R$150K, 1-2 months (Edital Parser)

**Expected ROI:** Reduces legal analysis cost from R$2,000 to ~R$50 per property; scales from 20 to 200 analyses per month

### Pattern 3: Automated Valuation Model (AVM)

**Problem:** Property valuation demands cross-referencing FipeZap, OLX, ZAP, and QuintoAndar data by hand, taking approximately 4 hours per property.

**Solution Architecture:**
Comparable sales data -> feature engineering -> gradient boosting/neural net model -> confidence interval output

**Vertical-Specific Details:**
- Integrates FipeZap, OLX, ZAP, VivaReal, QuintoAndar comparables with auction properties
- Feature engineering on: m2, bedrooms, location, floor, condition
- Output: estimated market value, discount percentage, confidence score
- Must account for auction-specific discount patterns (30-60% below market)

**Cross-Vertical Pattern:** See `kb/patterns/scoring-engines.md`

**Estimated Effort:** R$150K-R$250K, 2-3 months

**Expected ROI:** Reduces valuation time from 4 hours to 30 seconds per property; increases deal flow screening by 50x; improves bid accuracy by 25%

### Pattern 4: Investment Scoring (Multi-Factor Composite)

**Problem:** Investors lack a systematic way to compare auction opportunities across dimensions (price, risk, location, occupancy, liquidity).

**Solution Architecture:**
Multi-factor model (price discount x legal risk x occupancy x location quality x liquidity x reform cost) -> weighted composite score

**Vertical-Specific Details:**
- Combines AVM output + legal risk score + location analytics + occupancy data
- Investor-facing UI with map visualization (Mapbox), alerts, and portfolio tracking
- Enables institutional-grade deal screening at individual investor cost
- Configurable weights per investor risk profile

**Cross-Vertical Pattern:** See `kb/patterns/scoring-engines.md`

**Estimated Effort:** R$120K-R$200K, 2-3 months

**Expected ROI:** Systematic screening replaces ad hoc evaluation; enables scaling from dozens to hundreds of properties reviewed

### Pattern 5: Alert/Notification System

**Problem:** New auction listings appear across 1,000+ sites with no centralized notification. Investors miss opportunities due to lack of real-time visibility.

**Solution Architecture:**
Event-driven architecture (Kafka/RabbitMQ) -> user preference matching -> WhatsApp Business API/email -> engagement tracking

**Vertical-Specific Details:**
- NLP extraction of key terms, deadlines, payment conditions from PDF editais
- Push alerts via WhatsApp Business API and email based on investor criteria (location, price range, property type, discount threshold)
- Fastest time-to-value project; addresses the #1 investor pain point
- Users receive matching opportunities within 15 minutes of listing

**Cross-Vertical Pattern:** See `kb/patterns/alerting.md`

**Estimated Effort:** R$80K-R$150K, 1-2 months

**Expected ROI:** Early access increases successful arrematacao rate by 35%

### Pattern 6: Workflow Automation (Post-Arrematacao)

**Problem:** Post-auction processes (desocupacao, documentation, registration) are complex, multi-step, and tracked manually.

**Solution Architecture:**
Post-arrematacao task templates -> document checklist -> deadline tracking -> CRM integration -> status dashboard

**Vertical-Specific Details:**
- Template-based workflows for each auction type (judicial, extrajudicial, Caixa)
- Automated document checklists and deadline reminders
- Status tracking across the full post-auction lifecycle
- Integration with cartorio and TJ systems where available

**Estimated Effort:** Included in broader platform implementations

**Expected ROI:** Reduces time-to-registration from 9 months to 4 months; automates 60% of post-arrematacao tasks

## Implementation Projects

| Project | Price Range | Duration | Key Deliverables |
|---------|-----------|----------|-----------------|
| Auction Aggregation Engine | R$250K-R$400K | 3-4 months | Unified database from 500+ sources, daily refresh, search/filter API, frontend |
| Automated Valuation Model (AVM) | R$150K-R$250K | 2-3 months | ML valuation model, market value estimate, discount %, confidence score |
| Legal Risk Scorer | R$200K-R$350K | 3-5 months | NLP edital parser, matricula OCR, risk score (0-100), flagged issues |
| Investment Scoring Dashboard | R$120K-R$200K | 2-3 months | Composite score, map visualization, alerts, portfolio tracking |
| Edital Parser and Alert System | R$80K-R$150K | 1-2 months | NLP extraction, WhatsApp/email alerts, 15-min notification SLA |

## Pricing (Cross-Vertical Comparison)

| Stage | Auctions | Mining | Investment | Insurance |
|-------|----------|--------|------------|-----------|
| Diagnostic | R$35K-75K | R$25K-75K | R$25K-80K | R$25K-75K |
| First implementation | R$80K-150K | R$150K-350K | R$100K-200K | R$200K-400K |
| Full 12-month portfolio | R$800K-1.35M | R$1.3M-3M | R$650K-1.25M | R$1.5M-3M |
| Ongoing retainer | R$15K-40K/mo | R$30K-80K/mo | R$15K-40K/mo | R$25K-60K/mo |

## Technology Recommendations

See [tech-landscape.md](tech-landscape.md) for the full recommended stack. Key choices:

- **Scraping**: Playwright/Puppeteer for JS-heavy sites with rotating proxies
- **Storage**: PostgreSQL + Elasticsearch for structured + full-text search
- **OCR**: Azure AI Document Intelligence or Tesseract
- **NLP**: Portuguese-trained LLMs (GPT-4/Claude) for legal text interpretation
- **Frontend**: React/Next.js with Mapbox for geolocation visualization
- **Messaging**: Kafka/RabbitMQ for real-time alert processing
- **Caching**: Redis for high-frequency data access

## Data Architecture

```
[1,000+ Leiloeiro Sites] --scraping--> [Scrapy/Playwright Cluster]
[Caixa API via Apify]   --API-------> |
[Santander API via Apify]--API-------> |
[TJ Databases (27)]     --scraping--> |
                                       v
                              [ETL Pipeline]
                                       |
                    +------------------+------------------+
                    v                  v                  v
            [PostgreSQL]      [Elasticsearch]        [Redis]
            (structured)      (full-text search)     (cache)
                    |                  |
                    v                  v
              [Search/Filter API + Scoring Engine]
                    |
          +---------+---------+---------+
          v         v         v         v
      [Frontend] [Alerts]  [AVM]   [Legal Risk]
      (React/    (Kafka/   (ML     (OCR/NLP
       Next.js/  RabbitMQ/ model)   pipeline)
       Mapbox)   WhatsApp)
```

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
