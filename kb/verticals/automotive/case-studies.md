---
title: "Automotive — Case Studies"
type: case-studies
vertical: automotive
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [automotive, case-studies, outcomes, roi, valuation, inventory, deixacomigo]
---

# Automotive — Case Studies

## Case 0: deixacomigo — Vehicle Valuation & Lead Capture Tool (Internal Project)

**Client Profile:** AI Ventures internal project / consignment broker tool
**Engagement Type:** Product build (owned asset)
**Duration:** 3 weeks initial build, ongoing iteration
**Investment:** Internal development time

### Challenge

Consignment brokers targeting premium used car owners (R$60K–R$120K+ vehicles) needed a tool to demonstrate pricing credibility. Car owners are typically lowballed by dealers at 75–85% of FIPE. Without data, owners can't see the concrete benefit of consignment vs. direct sale to a dealer, and brokers lack a systematic lead capture mechanism.

### Approach

1. Built a vehicle valuation engine integrating FIPE/Parallelum API with Supabase caching for fast, reliable price lookups
2. Developed a 6-factor pricing algorithm: brand prestige, vehicle age, mileage, condition, regional demand, and commission structure
3. Implemented consignment aptitude classification (ideal/viable/marginal) to qualify leads automatically
4. Created a mobile-first valuation form with cascading brand > model > year selection
5. Built lead capture integrated with valuation results, persisted in Supabase with Resend email notifications to the broker

### Results

| Metric | Outcome | Notes |
|--------|---------|-------|
| FIPE API integration | Reliable with cache fallback | Parallelum v2 with Supabase cache layer |
| Valuation factors | 6 calibrated factors | Brand, age, km, condition, regional demand, commission |
| Lead qualification | 3-tier classification | Ideal / Viable / Marginal consignment |
| Time to valuation | <3 seconds | Cached FIPE data + client-side computation |
| Technical SEO | Complete | Sitemap, robots.txt, OpenGraph, Schema.org |

### Key Learnings

- **FIPE/Parallelum API is reliable but needs caching**: Rate limits and occasional downtime require a cache layer (Supabase works well)
- **6-factor pricing is a good starting framework but needs expansion for dealer use**: Production dealer implementations need 10–15 factors and make/model-specific depreciation curves
- **Lead capture must be frictionless**: Embedding lead capture into the valuation result (not a separate step) dramatically improves conversion
- **Consignment aptitude classification adds credibility**: Showing "marginal" for some vehicles (instead of always saying "consign!") builds trust
- **The stack is reusable**: Next.js + Supabase + FIPE/Parallelum + Resend is a proven foundation for all automotive pricing tools

### Reusable Assets

- FIPE/Parallelum API integration with Supabase caching (TypeScript)
- 6-factor pricing algorithm with guard rails
- Lead capture form with cascading vehicle selection
- Email notification pipeline (Resend)
- Technical SEO framework for vehicle-related pages

---

## Case 1: Multi-Brand Dealership — Pricing & Inventory Optimization

**Client Profile:** Multi-brand dealership, ~250 vehicles in stock, R$30M annual revenue, São Paulo interior
**Engagement Type:** Diagnostic + Implementation (Valuation Engine + Inventory Dashboard)
**Duration:** 5–7 months (diagnostic + two overlapping projects)
**Investment:** R$200K–R$400K (combined)

### Challenge

The dealership priced vehicles using FIPE + owner intuition, with the Director personally approving every acquisition and listing price. Average days-on-lot was 72 days (well above the 45-day industry target), with 30% of inventory over 90 days old. Floor plan financing at 13.25% SELIC was costing ~R$1,200/vehicle/month, totaling R$300K/month in carrying costs for the entire stock. Approximately 8% of vehicles sold below acquisition cost (losses), representing ~R$400K/year in margin destruction.

### Approach

1. **Diagnostic** (2 weeks): Audited last 200 transactions; mapped pricing process; identified that 65% of pricing decisions had no marketplace comparison
2. **Valuation Engine** (3 months): Built multi-factor pricing model using FIPE + OLX/Webmotors comparables + regional demand data + condition scoring; integrated as a pricing recommendation tool for the acquisition team
3. **Inventory Dashboard** (3 months, overlapping): Built real-time dashboard showing every vehicle's age, carrying cost, marketplace positioning (price vs. competitors), and recommended actions

### Results

| Metric | Before | After | Impact |
|--------|--------|-------|--------|
| Average days-on-lot | 72 days | 48 days | 33% reduction |
| Vehicles over 90 days | 30% of stock | 12% of stock | 60% reduction in aged inventory |
| Monthly floor plan cost | R$300K | R$200K | R$100K/month savings (R$1.2M/year) |
| Vehicles sold at loss | 8% of transactions | 3% of transactions | 63% reduction in loss sales |
| Average gross margin per vehicle | R$4,200 | R$5,800 | 38% margin improvement |
| Annual margin impact | — | +R$400K (carrying savings) + R$320K (margin improvement) | R$720K/year total impact |

### Key Learnings

- The Director was the bottleneck — by providing data-driven pricing recommendations, the team could make faster decisions without waiting for his review of each vehicle
- Marketplace comparison was the single highest-impact feature — showing "your car is priced 12% above the 15 comparable listings on Webmotors" drove immediate price adjustments
- Aging alerts at 30/60/90 days created urgency that didn't exist before — "this car has cost you R$3,600 in floor plan since you bought it" is a powerful motivator
- Regional demand data (DENATRAN transfers by municipality) helped guide acquisitions — "pickup trucks sell 2x faster in this region than sedans"

### Reusable Assets

- Multi-factor pricing model (adaptable to any dealer's market segment)
- OLX/Webmotors scraper framework
- Inventory health scoring algorithm
- Floor plan cost integration module

---

## Case 2: Consignment Platform — White-Label Valuation Tool

**Client Profile:** Consignment platform, ~80 vehicles under mandate, R$8M annual revenue, São Paulo
**Engagement Type:** White-label deixacomigo deployment + customization
**Duration:** 3 weeks (deployment) + ongoing retainer
**Investment:** R$35K (setup) + R$5K/month (retainer)

### Challenge

The platform struggled to win consignment mandates from premium car owners. Owners were skeptical of consignment value — they compared the consignment commission (5–7%) against the simplicity of selling to a dealer (even at 75–85% FIPE). The platform had no tool to demonstrate, with data, that consignment nets more money.

### Approach

1. Deployed white-label deixacomigo with custom branding, domain, and color scheme
2. Calibrated pricing algorithm for premium vehicle segment (R$80K–R$250K)
3. Customized the comparison view: "sell to dealer" vs. "consign with us" with net-to-owner calculation
4. Integrated lead capture with platform's CRM (HubSpot) via webhook
5. Added Google Analytics + conversion tracking for marketing team

### Results

| Metric | Before | After | Impact |
|--------|--------|-------|--------|
| Monthly valuation requests | 0 (no tool) | 340+ | New lead channel |
| Valuation-to-mandate conversion | N/A | 12% | ~40 new mandates/month from tool |
| Average vehicle value (mandated via tool) | N/A | R$95K | Premium segment as designed |
| Monthly commission revenue from tool leads | R$0 | R$120K–R$200K | At 5% commission on R$95K avg |
| Cost per lead (from tool) | N/A | R$15 (hosting + retainer / leads) | vs. R$80–R$150 for paid ads |

### Key Learnings

- **Speed of deployment is a selling point**: 3 weeks from contract to live tool; clients are impressed
- **The comparison view is the conversion driver**: Showing "dealer offer: R$68K" vs. "consignment net: R$82K" with the exact math is what converts
- **Premium vehicles are the sweet spot**: Commission on R$80K+ vehicles justifies the tool cost easily
- **CRM integration is essential**: Without automatic lead push to the platform's existing workflow, leads were lost
- **Retainer pays for itself**: Monthly algorithm calibration + scraper maintenance keeps pricing accurate; when the tool shows stale prices, conversions drop

### Reusable Assets

- White-label deployment playbook (3-week timeline)
- CRM webhook integration template (HubSpot, Pipedrive)
- Premium vehicle pricing calibration profile
- Conversion tracking setup guide

---

## Case 3: Vehicle-Backed Fintech — Collateral Valuation Engine

**Client Profile:** Fintech offering vehicle-backed personal loans (CDC auto / refinancing), R$200M loan portfolio, nationwide
**Engagement Type:** Implementation (Vehicle Credit Risk Scoring)
**Duration:** 4 months
**Investment:** R$180K

### Challenge

The fintech used FIPE-only for collateral valuation, setting maximum LTV at 70% of FIPE. When borrowers defaulted and vehicles were repossessed, actual recovery at auction averaged 62% of FIPE — meaning effective LTV was 112% (underwater). The 8-point gap between assumed and actual recovery was creating portfolio losses of ~R$3M/year on a R$200M book.

### Approach

1. Built multi-factor collateral valuation model: FIPE base + condition adjustment + regional demand factor + forced-sale discount model
2. Trained forced-sale discount model on 5,000+ auction result records (partnered with auction house for historical data)
3. Created depreciation forecast module: predicted vehicle value at 6/12/24-month horizons for LTV stress testing
4. Deployed as API endpoint integrated into the fintech's loan origination system

### Results

| Metric | Before | After | Impact |
|--------|--------|-------|--------|
| Collateral valuation method | FIPE-only | Multi-factor (FIPE + 4 adjustments) | Realistic collateral values |
| Average recovery vs. valuation | 62% of FIPE (vs. 70% LTV assumption) | 91% of model valuation | Valuation now predicts actual recovery |
| Portfolio loss from collateral shortfall | ~R$3M/year | ~R$800K/year | 73% reduction in collateral-related losses |
| Loan approval accuracy | 85% (too many underwater loans approved) | 93% | Better risk selection |
| API response time | N/A (manual FIPE lookup) | <500ms per valuation | Integrated into real-time loan origination |

### Key Learnings

- **Forced-sale discount varies dramatically by vehicle**: Popular models (HB20, Onix) have 10–12% discount; luxury brands 20–30%; regional variation adds another 5–10%
- **Auction data is gold**: Historical auction results provide the ground truth for forced-sale pricing that FIPE cannot
- **Depreciation forecast is the second-highest-value feature**: Stress testing LTV at future dates prevents approving loans that become underwater as the vehicle depreciates
- **Model needs quarterly retraining**: Market conditions shift; depreciation curves change with new model launches

### Reusable Assets

- Forced-sale discount model (by make/model/region)
- Depreciation forecast module (6/12/24 month horizons)
- Auction result ingestion pipeline
- LTV stress testing framework

---

## Quantified Outcomes Library

| Outcome Category | Range | Evidence Source |
|-----------------|-------|---------------|
| Average days-on-lot reduction | 72 → 48 days (33% reduction) | Case 1: multi-brand dealership |
| Monthly floor plan savings | R$100K/month (R$1.2M/year) | Case 1: multi-brand dealership |
| Loss sale reduction | 8% → 3% of transactions | Case 1: multi-brand dealership |
| Gross margin per vehicle improvement | R$4,200 → R$5,800 (38%) | Case 1: multi-brand dealership |
| Valuation-to-mandate conversion | 12% | Case 2: consignment platform |
| Cost per lead (valuation tool) | R$15 vs. R$80–R$150 paid ads | Case 2: consignment platform |
| Monthly commission from tool leads | R$120K–R$200K | Case 2: consignment platform |
| Collateral loss reduction | R$3M → R$800K/year (73%) | Case 3: vehicle-backed fintech |
| Recovery vs. valuation accuracy | 62% → 91% of model value | Case 3: vehicle-backed fintech |
| White-label deployment time | 3 weeks to live | Case 2: consignment platform |
| FIPE API response (with cache) | <3 seconds | Case 0: deixacomigo |

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
