---
title: "Automotive — Solution Patterns"
type: solution-patterns
vertical: automotive
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [automotive, solutions, technical, patterns, valuation, inventory, fleet]
---

# Automotive — Solution Patterns

## Reusable Solution Components

### Pattern 1: Multi-Factor Vehicle Valuation Engine

**Problem:** The entire Brazilian used car market anchors on FIPE monthly reference prices, but FIPE does not reflect regional demand, vehicle condition, mileage, color, or real-time market dynamics. Dealers overpay on acquisition and underprice on sale because they lack data beyond gut feeling + FIPE.

**Solution Architecture:**
FIPE/Parallelum API (base reference) + marketplace scrapers (OLX/Webmotors comparable listings) + DENATRAN frota data (regional demand) + vehicle condition input (manual or LLM vision) + km adjustment curves → ML ensemble model → recommended acquisition price, listing price, expected days-to-sell, and consignment viability score

**Vertical-Specific Details:**
- Must handle all FIPE categories: carros, utilitários, motos, caminhões
- Regional price variation of 10–20% (e.g., pickup trucks command premium in agro regions; compact cars in São Paulo)
- Condition adjustment factors: mechanical, cosmetic, tire, interior, documentation (5-axis scoring)
- Mileage depreciation curves are non-linear and brand-specific (Toyota/Honda retain value differently than domestic brands)
- deixacomigo implements a simplified version with 6 calibrated factors: brand, age, km, condition, regional demand, commission

**Cross-Vertical Pattern:** See `kb/patterns/predictive-models.md` (ML pricing/valuation pattern)

**Estimated Effort:** R$80,000–R$200,000, 2–4 months

**Expected ROI:** 5–15% improvement in acquisition margin; 20–30% reduction in days-on-lot through better pricing

### Pattern 2: Dealer Inventory Intelligence Dashboard

**Problem:** Dealers manage 50–500 vehicles with spreadsheets or basic DMS. No automated alerts for aging inventory, no visibility into which vehicles are priced above or below market, no demand forecasting to guide acquisitions.

**Solution Architecture:**
DMS/inventory data + FIPE pricing + marketplace comparables (OLX/Webmotors) + floor plan cost calculator → real-time dashboard showing: inventory health score, aging alerts, price-vs-market positioning, demand forecast by model, recommended price adjustments

**Vertical-Specific Details:**
- Floor plan cost integration: at SELIC ~13.25%, each vehicle accrues R$500–R$2,000/month in financing cost; dashboard must show margin erosion by day
- Marketplace comparison: for each vehicle in stock, show number of competing listings, median listing price, and price positioning (percentile)
- Aging thresholds: configurable alerts at 30, 60, 90 days; recommended price reduction percentages at each threshold
- Acquisition recommendations: based on demand forecast, suggest which makes/models/years to acquire next

**Cross-Vertical Pattern:** Same dashboard pattern serves inventory management in auctions (leilão lots) and fleet management

**Estimated Effort:** R$100,000–R$250,000, 3–5 months

**Expected ROI:** 15–25% reduction in average days-on-lot; R$500–R$2,000 saved per vehicle in carrying costs; 10–20% increase in inventory turnover rate

### Pattern 3: Auto Insurance Lead Generation Engine

**Problem:** Used car sales are a natural trigger for auto insurance purchases, but dealers and consignment platforms don't systematically capture or monetize this lead flow. Insurance brokers pay R$50–R$200 per qualified auto insurance lead.

**Solution Architecture:**
Vehicle sale/valuation event → customer data capture → insurance need scoring (vehicle value, profile, existing coverage check) → lead qualification → distribution to partner insurance brokers/insurers via API or CRM → commission tracking

**Vertical-Specific Details:**
- Every used car transaction is an insurance event — buyer needs new policy, seller may cancel existing
- Lead value correlates with vehicle FIPE value: R$80K+ vehicles = premium insurance leads
- Integration with SUSEP open data for insurance market intelligence
- deixacomigo's lead capture funnel is directly extensible to insurance lead generation
- Can be offered as white-label to dealer networks, generating recurring referral commission

**Cross-Vertical Pattern:** Same lead generation pattern applies to insurance-surety vertical (see `kb/verticals/insurance-surety/solution-patterns.md`)

**Estimated Effort:** R$60,000–R$150,000, 2–3 months

**Expected ROI:** R$50–R$200 per qualified lead; at 100 leads/month = R$5K–R$20K/month in referral revenue for the dealer/platform

### Pattern 4: Fleet Management Analytics Platform

**Problem:** Fleet managers (locadoras, corporate fleets, government fleets) lack data-driven tools for optimal replacement timing, TCO analysis, and disposal pricing. Decisions are calendar-based ("replace at 36 months") rather than optimized for total cost.

**Solution Architecture:**
Fleet vehicle data (make/model/year/km/maintenance history) + FIPE depreciation curves + fuel consumption data + maintenance cost models + disposal market pricing → TCO optimization model → recommended replacement month, optimal disposal channel (auction, direct sale, trade-in), expected disposal value

**Vertical-Specific Details:**
- Brazil's largest fleet operators (Localiza ~600K vehicles, Movida ~200K vehicles) already have sophisticated systems; mid-market targets are corporate fleets (100–5,000 vehicles)
- TCO components: depreciation + fuel + maintenance + insurance + IPVA + financing cost
- Optimal replacement point is where cumulative maintenance + depreciation cost exceeds replacement benefit
- Disposal channel optimization: auction (fast, lower price), direct sale (slower, higher price), consignment (medium)
- Regional variation in disposal value: same vehicle sells for different prices in different states

**Cross-Vertical Pattern:** TCO analysis pattern reusable in mining (heavy equipment fleet) and construction

**Estimated Effort:** R$150,000–R$350,000, 4–6 months

**Expected ROI:** R$3,000–R$8,000 savings per vehicle per replacement cycle; on a 500-vehicle fleet = R$1.5M–R$4M per cycle

### Pattern 5: Vehicle Credit Risk Scoring Engine

**Problem:** Fintechs offering vehicle-backed credit (CDC auto, refinancing, consórcio) rely on FIPE-only for collateral valuation. FIPE doesn't account for condition, regional market, or forced-sale discount (typically 15–25% below retail). This creates LTV blind spots that manifest as losses when borrowers default and collateral is liquidated.

**Solution Architecture:**
Vehicle data (make/model/year/km/condition) + FIPE reference + marketplace pricing (OLX/Webmotors) + regional demand data (DENATRAN) + historical auction results (forced-sale prices) → ML model → estimated retail value, estimated forced-sale value, depreciation forecast (6/12/24 months), recommended LTV ceiling, risk tier

**Vertical-Specific Details:**
- Forced-sale discount varies by vehicle: popular models (HB20, Onix, Kwid) have 10–15% discount; luxury/niche models have 20–30% discount
- Depreciation forecast must account for model refresh cycles (new model launch = accelerated depreciation of prior generation)
- EV-specific risk: battery degradation, range loss, and rapid model obsolescence create novel depreciation curves with limited historical data
- Integration with alienação fiduciária registry (DETRAN) to check existing liens
- Must comply with Banco Central Resolução 4.893/2021 collateral valuation requirements

**Cross-Vertical Pattern:** Credit risk scoring pattern reusable in insurance-surety (tomador risk), real-estate (property collateral)

**Estimated Effort:** R$100,000–R$250,000, 3–5 months

**Expected ROI:** 10–20% improvement in collateral recovery rates; reduction in portfolio LGD (Loss Given Default)

## Implementation Projects

| Project | Price Range | Duration | Key Deliverables |
|---------|-----------|----------|-----------------|
| Vehicle Valuation Engine | R$80K–R$200K | 2–4 months | Multi-factor pricing model, FIPE/Parallelum integration, marketplace scraper, condition assessment module, API endpoint |
| Dealer Inventory Intelligence | R$100K–R$250K | 3–5 months | Real-time dashboard, aging alerts, marketplace comparison, demand forecast, floor plan cost tracker |
| Auto Insurance Lead Gen | R$60K–R$150K | 2–3 months | Lead capture funnel, insurance need scoring, broker distribution API, commission tracking |
| Fleet Management Analytics | R$150K–R$350K | 4–6 months | TCO model, replacement optimization, disposal channel recommendation, fleet health dashboard |
| Vehicle Credit Risk Scoring | R$100K–R$250K | 3–5 months | Collateral valuation model, forced-sale pricing, depreciation forecast, LTV recommendation, risk tier API |

## Technology Recommendations

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| Data Ingestion | FIPE/Parallelum API + custom marketplace scrapers (Playwright/Puppeteer) + DENATRAN API connectors | Multi-source pricing data; marketplace scraping for real-time comparables |
| Storage | Supabase (PostgreSQL) + cache layer (Redis) | Proven in deixacomigo; FIPE data caching reduces API costs and latency |
| Processing | Python ML pipeline (scikit-learn, XGBoost, LightGBM) + Node.js/TypeScript business logic | Pricing models + application logic; consistent with deixacomigo stack |
| Analytics | Metabase or custom dashboards (Next.js + Tremor/Recharts) | Dealer-facing dashboards; mobile-responsive for on-the-floor use |
| API Layer | REST API (Next.js API routes or standalone) + webhook notifications | Integration with dealer DMS, fintech platforms, insurance brokers |
| AI/Vision | Claude API or GPT-4V for vehicle photo condition assessment | LLM vision for photo-based condition grading |
| Infrastructure | Vercel (application) + Supabase (database) + AWS Lambda (scrapers) | Consistent with deixacomigo deployment; scales with demand |

## Data Architecture

Typical data flow for an automotive dealer engagement:

```
External Sources                    Internal Systems              AI Layer
─────────────────                  ─────────────────             ─────────
FIPE/Parallelum   ──┐              Dealer DMS      ──┐          ┌─ Valuation Model
OLX/Webmotors     ──┤              Floor Plan Fin. ──┤          ├─ Inventory Score
DENATRAN/SENATRAN ──┼──→ Data Lake ←──────────────────┤──→ ML ──┤
DETRAN APIs       ──┤              CRM             ──┤          ├─ Demand Forecast
IBGE Regional     ──┤              Sales History   ──┘          ├─ Condition Score
Vehicle Photos    ──┘                                           └─ Lead Score
                                                                     │
                                                                     ▼
                                                              Dealer Dashboard
                                                              Pricing API
                                                              Lead Distribution
                                                              Inventory Alerts
```

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
