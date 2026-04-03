---
title: "Automotive — Engagement Templates"
type: engagement-templates
vertical: automotive
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [automotive, diagnostic, implementation, engagement, valuation, inventory]
---

# Automotive — Engagement Templates

## Diagnostic Engagement (Paid Assessment)

**Price Range:** R$15,000–R$40,000
**Duration:** 2–3 weeks
**Deliverables:** Pricing & Valuation Audit, Inventory Health Assessment, Data Integration Maturity Report, 6/12-Month Implementation Roadmap

### Week-by-Week Breakdown

#### Week 1: Discovery

- **Stakeholder interviews**: Owner/Director, Sales Manager, Vehicle Evaluator/Buyer, Financial Controller (floor plan)
- **Pricing workflow mapping**: Map current valuation process from vehicle arrival through pricing to listing — how are acquisition prices set? Who decides? What data is used?
- **Inventory audit**: Current stock count, average days-on-lot, aging distribution, floor plan cost structure
- **Technology audit**: Inventory DMS (or Excel), CRM, marketplace listing tools, financial systems
- **Data source inventory**: FIPE usage, marketplace monitoring (if any), condition assessment process

#### Week 2: Assessment

- **Pricing accuracy measurement**:
  - Compare last 50 acquisition prices against actual sale prices — what was the average margin?
  - Compare last 50 listing prices against marketplace median — are they priced competitively?
  - Identify vehicles that sold below acquisition cost (losses) — what went wrong?
- **Inventory turnover analysis**:
  - Average days-on-lot by vehicle category (economy, mid-range, premium, trucks/SUVs)
  - Floor plan cost per vehicle per month
  - Total monthly carrying cost (floor plan + overhead allocation)
  - Vehicles currently over 60 days — how many and what's the total capital locked?
- **Lead conversion audit** (if applicable):
  - Walk-in to sale conversion rate
  - Online inquiry to visit conversion rate
  - Lead response time (hours? days?)
  - Insurance/financing attach rate per sale
- **Condition assessment review**:
  - How are vehicles evaluated today? (visual, mechanical, documentation)
  - How consistent is grading across evaluators?
  - How does condition factor into pricing?

#### Week 3: Analysis & Recommendations

- Gap analysis: current pricing methodology vs. data-driven best practice
- Quantify margin leakage: overpayment on acquisition, underpricing on listing, carrying cost from slow turnover
- Priority matrix: quick wins (<30 days) vs. strategic initiatives (3–6 months)
- ROI projections for top 3 initiatives
- 6/12-month implementation roadmap with specific project scopes and pricing

### Discovery Questions

1. How do you determine the price you'll pay for a vehicle? Walk me through the last car you bought.
2. What tools/data sources do you use for pricing? (FIPE only? Marketplace comparison? Gut feeling?)
3. What is your average days-on-lot? Do you know this number off the top of your head, or would you need to calculate it?
4. How much are you paying in floor plan interest per month across your entire inventory?
5. How many vehicles in your current stock have been there over 60 days? Over 90 days?
6. When a vehicle hits 60 days, what happens? Is there a systematic price reduction process?
7. How do you list vehicles on marketplaces (OLX, Webmotors)? Manual or automated? How often are prices updated?
8. How do you evaluate vehicle condition? Is the process standardized across your team?
9. Do you capture leads from online inquiries systematically? What's your response time?
10. What percentage of your buyers also finance through you or purchase insurance through you?

### Assessment Dimensions

| Dimension | What We Measure | Scoring Criteria (1–5) |
|-----------|----------------|----------------------|
| Pricing Sophistication | Data sources used, pricing methodology, regional/condition adjustments | 1=FIPE only, 5=multi-factor model with real-time marketplace data |
| Inventory Management | Days-on-lot tracking, aging alerts, turnover optimization | 1=no tracking (Excel/memory), 5=real-time dashboard with automated alerts |
| Lead Management | Capture, qualification, response time, conversion tracking | 1=no systematic capture, 5=automated funnel with CRM integration |
| Condition Assessment | Standardization, consistency, documentation | 1=subjective by individual, 5=standardized multi-axis with photo documentation |
| Marketplace Presence | Listing quality, pricing competitiveness, update frequency | 1=manual, infrequent listings, 5=automated, optimized, real-time pricing |
| Ancillary Revenue | Insurance, financing, extended warranty attach rates | 1=no attach, 5=systematic monetization of every transaction |

## Implementation Engagements

### Implementation 1: Vehicle Valuation Engine

**Price Range:** R$80,000–R$200,000
**Duration:** 2–4 months
**Prerequisites:** Diagnostic completed
**Deliverables:** Multi-factor pricing model, FIPE/Parallelum API integration, marketplace comparables module, condition assessment framework, pricing API endpoint

#### Phase Breakdown

1. **Data integration (Weeks 1–4)**: Connect FIPE/Parallelum API (leveraging deixacomigo's proven integration); build marketplace scrapers for OLX/Webmotors; integrate DENATRAN regional frota data
2. **ML model development (Weeks 3–8)**: Train pricing model on historical transaction data + marketplace comparables; calibrate regional, condition, and mileage adjustment factors; validate against known sale outcomes
3. **Condition assessment module (Weeks 4–10)**: Implement standardized 5-axis condition scoring (mechanical, cosmetic, tires, interior, documentation); optional LLM vision integration for photo-based assessment
4. **API and dashboard (Weeks 8–14)**: Build pricing API for integration with dealer DMS; create evaluator-facing pricing dashboard with price recommendation, confidence interval, and comparable listings
5. **Testing and calibration (Weeks 12–16)**: Parallel run with existing pricing process; measure accuracy vs. actual sale outcomes; calibrate model; full deployment

**Key Learning from deixacomigo:** The 6-factor pricing algorithm (brand, age, km, condition, regional demand, commission) provides a proven starting framework. Production dealer implementations need finer granularity: 10–15 factors, make/model-specific depreciation curves, and continuous calibration against sale outcomes.

### Implementation 2: Dealer Inventory Intelligence Dashboard

**Price Range:** R$100,000–R$250,000
**Duration:** 3–5 months
**Prerequisites:** Diagnostic completed; ideally paired with Valuation Engine
**Deliverables:** Real-time inventory dashboard, aging alert system, marketplace price positioning, demand forecast, floor plan cost tracker

#### Phase Breakdown

1. **DMS integration (Weeks 1–4)**: Connect to dealer's inventory management system (or build lightweight inventory tracker if none exists); ingest vehicle data, acquisition dates, costs
2. **Floor plan cost model (Weeks 2–6)**: Integrate floor plan financing terms; calculate per-vehicle per-day carrying cost; build margin erosion projections
3. **Marketplace intelligence (Weeks 4–10)**: Automated comparison of each vehicle in stock against marketplace listings; competitive pricing analysis; demand indicators
4. **Dashboard build (Weeks 8–16)**: Real-time inventory health score; aging waterfall chart; price-vs-market positioning for each vehicle; recommended price adjustments; acquisition recommendations
5. **Alert system (Weeks 14–20)**: Automated alerts for aging thresholds (30/60/90 days); price adjustment recommendations; demand shift notifications

### Implementation 3: Auto Insurance Lead Generation Engine

**Price Range:** R$60,000–R$150,000
**Duration:** 2–3 months
**Prerequisites:** Diagnostic completed
**Deliverables:** Lead capture funnel, insurance need scoring model, broker distribution API, commission tracking dashboard

#### Phase Breakdown

1. **Lead capture integration (Weeks 1–3)**: Embed insurance lead capture into existing vehicle sale/valuation flow; build on deixacomigo's proven lead capture architecture (Supabase + Resend)
2. **Insurance need scoring (Weeks 2–5)**: Score leads based on vehicle value, buyer profile, existing coverage indicators; prioritize high-value leads (R$80K+ vehicles)
3. **Broker distribution (Weeks 4–8)**: Build API for distributing qualified leads to partner insurance brokers; match leads to broker specialization (auto, premium, fleet)
4. **Commission tracking (Weeks 6–10)**: Track referral commissions; dashboard showing lead volume, conversion rates, revenue per lead

### Implementation 4: Fleet Management Analytics Platform

**Price Range:** R$150,000–R$350,000
**Duration:** 4–6 months
**Prerequisites:** Diagnostic completed
**Deliverables:** TCO model per vehicle, replacement optimization engine, disposal channel recommendation, fleet health dashboard

### Implementation 5: Vehicle Credit Risk Scoring Engine

**Price Range:** R$100,000–R$250,000
**Duration:** 3–5 months
**Prerequisites:** Diagnostic completed
**Deliverables:** Collateral valuation model (retail + forced-sale), depreciation forecast, LTV recommendation API, risk tier classification

## Engagement Arc (Full Journey)

```
Diagnostic → 1st Implementation → Expansion → Retainer
(R$15–40K)   (R$80–250K)          (R$60K–350K)  (R$10–30K/mo)
```

Typical arc:
1. **Diagnostic** (2–3 weeks): Pricing audit + inventory health assessment
2. **1st Implementation** (2–4 months): Usually Vehicle Valuation Engine (highest pain, fastest ROI, proven by deixacomigo)
3. **Expansion** (2–6 months): Inventory Intelligence Dashboard, Insurance Lead Gen, or Credit Risk Scoring
4. **Retainer** (ongoing): Model retraining, marketplace scraper maintenance, dashboard updates, new feature development

## Retainer Model

**Monthly Price:** R$10,000–R$30,000
**Includes:**
- ML model monitoring and retraining (monthly or as market conditions shift)
- Marketplace scraper maintenance (OLX/Webmotors change DOM structure frequently)
- FIPE data refresh and integration monitoring
- Dashboard updates and new features
- Priority support for pricing and inventory questions
- Monthly analytics review with actionable recommendations

**SLA:** 8-hour response for critical issues (pricing model down, scraper broken), 24-hour for standard requests

## White-Label deixacomigo Deployment

A distinct engagement path leverages the existing deixacomigo codebase:

**Price:** R$20,000–R$40,000 (setup) + R$3,000–R$8,000/month (retainer)
**Duration:** 2–3 weeks to deploy
**Deliverables:** Branded vehicle valuation tool, lead capture funnel, email notifications, custom domain

This is a fast-deploy option for consignment platforms and dealer groups that want a customer-facing valuation tool without building from scratch. Leverages the entire deixacomigo stack (Next.js, Supabase, FIPE/Parallelum, Resend) with custom branding, pricing algorithm calibration for the client's market segment, and CRM integration.

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
