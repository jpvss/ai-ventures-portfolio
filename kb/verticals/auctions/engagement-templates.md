---
title: "Auction Market — Engagement Templates"
type: engagement-templates
vertical: auctions
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [auctions, diagnostic, implementation, engagement, AI-readiness]
---

# Auction Market — Engagement Templates

## Diagnostic Engagement (Paid Assessment)

**Price Range:** R$35,000-R$75,000
**Duration:** 2-3 weeks
**Target Clients:** Auction platforms/leiloeiros, investor groups/funds, advisory firms
**Deliverables:** Current-state assessment with data flows, AI Readiness Score (6 dimensions), 3-5 quick wins, strategic roadmap with ROI estimates, competitive benchmarking

### Week-by-Week Breakdown

#### Week 1: Discovery

**For auction platform/leiloeiro clients:**
- Assess current data sources and data coverage (how many auction platforms monitored)
- Evaluate platform architecture and technology stack age
- Review scraping capabilities and data freshness
- Map buyer experience flow end-to-end
- Assess API readiness and mobile experience

**For investor groups/funds:**
- Assess deal screening process (properties screened per week, conversion rate)
- Map legal analysis workflow (manual vs. automated edital/matricula analysis)
- Evaluate valuation methodology (what comparison data used, manual vs. automated)
- Review post-arrematacao management (desocupacao, documentation tracking)
- Map all data sources: how many auction platforms monitored, what comparison data used, how legal risk is assessed

#### Week 2: Assessment

Score AI readiness across **6 dimensions** (1-5 scale):

| Dimension | What We Measure | Scoring Criteria |
|-----------|----------------|-----------------|
| **Data Aggregation** | How many sources integrated, data freshness, coverage breadth | 1 = manual search on <10 sites; 5 = automated aggregation of 500+ sources with daily refresh |
| **Valuation Accuracy** | Current valuation method vs. AVM potential | 1 = gut feel/manual comps; 5 = ML-powered AVM with confidence intervals |
| **Legal Risk Assessment** | Manual vs. automated edital/matricula analysis | 1 = fully manual lawyer review at R$2,000/property; 5 = automated NLP scoring at R$50/property |
| **Deal Flow Efficiency** | Properties screened per week, conversion rate | 1 = <20 properties/week; 5 = 200+ properties/week with systematic scoring |
| **Technology Stack** | Platform age, API readiness, mobile experience | 1 = no platform/spreadsheets only; 5 = modern stack with APIs and mobile |
| **Post-Auction Workflow** | Desocupacao management, documentation tracking | 1 = fully manual/spreadsheet; 5 = automated workflow with deadline tracking |

Benchmark client against emerging AI tools (Leilao Ninja, BuscAI, Arremata.ai) to contextualize gaps.

#### Week 3: Recommendations

- Current-state assessment with data flow diagrams and technology gap analysis
- AI Readiness Score across 6 dimensions with visual scorecard
- 3-5 quick wins implementable within 30 days
- Strategic roadmap with ROI estimates for each recommended project
- Competitive benchmarking against market leaders and emerging AI tools

### Discovery Questions

**For platforms/leiloeiros:**
1. How many auction sources do you currently aggregate? What is your data refresh cadence?
2. What percentage of your listings include automated valuation data?
3. How do you handle edital parsing — manual or automated?
4. What is your current sell-through rate? How does it compare to the 15% market average?
5. What technology stack powers your platform? When was it last significantly updated?

**For investors/funds:**
1. How many properties do you screen per week? What is your current conversion rate?
2. How much do you spend on legal analysis per property? Per month?
3. What is your current valuation process? How long does it take per property?
4. How do you track post-arrematacao tasks and deadlines?
5. What is your average time from arrematacao to matricula registration?

## Implementation Engagements

### Implementation 1: Edital Parser and Alert System (Fastest Time-to-Value)

**Price Range:** R$80,000-R$150,000
**Duration:** 1-2 months
**Prerequisites:** Diagnostic completed
**Deliverables:** NLP extraction pipeline, WhatsApp Business API + email alert system, investor preference matching

#### Phase Breakdown
- **Phase 1 (Weeks 1-2):** PDF ingestion pipeline, OCR setup, NLP extraction model training
- **Phase 2 (Weeks 3-4):** Investor preference engine, matching algorithm, alert routing
- **Phase 3 (Weeks 5-8):** WhatsApp Business API integration, email templates, engagement tracking, testing

**ROI:** Users receive matching opportunities within 15 minutes of listing. Early access increases successful arrematacao rate by 35%.

### Implementation 2: Automated Valuation Model (AVM)

**Price Range:** R$150,000-R$250,000
**Duration:** 2-3 months
**Prerequisites:** Diagnostic completed; ideally Aggregation Engine in place or data sources identified
**Deliverables:** ML valuation model, API endpoint, confidence scoring, comparison dashboard

#### Phase Breakdown
- **Phase 1 (Weeks 1-3):** Data pipeline from FipeZap, OLX, ZAP, VivaReal, QuintoAndar
- **Phase 2 (Weeks 4-7):** Feature engineering (m2, bedrooms, location, floor, condition), model training
- **Phase 3 (Weeks 8-12):** API deployment, confidence calibration, frontend integration

**ROI:** Reduces valuation time from 4 hours to 30 seconds. Increases deal flow screening by 50x. Improves bid accuracy by 25%.

### Implementation 3: Auction Aggregation Engine (Foundation)

**Price Range:** R$250,000-R$400,000
**Duration:** 3-4 months
**Prerequisites:** Diagnostic completed
**Deliverables:** Unified database from 500+ sources, daily refresh, search/filter API, frontend

#### Phase Breakdown
- **Phase 1 (Weeks 1-4):** Scraping infrastructure (Scrapy/Playwright cluster, rotating proxies, CAPTCHA handling)
- **Phase 2 (Weeks 5-8):** ETL pipeline, data normalization, PostgreSQL + Elasticsearch setup
- **Phase 3 (Weeks 9-12):** Search/filter API, frontend, geocoding, map visualization
- **Phase 4 (Weeks 13-16):** Scaling to 500+ sources, monitoring, alerting, data quality checks

**ROI:** 10x more properties analyzed. Foundation for all other AI projects.

### Implementation 4: Legal Risk Scorer

**Price Range:** R$200,000-R$350,000
**Duration:** 3-5 months
**Prerequisites:** Diagnostic completed; Aggregation Engine recommended
**Deliverables:** NLP edital parser, matricula OCR pipeline, risk score (0-100), flagged issues dashboard

**ROI:** Reduces legal analysis cost from R$2,000 to ~R$50 per property. Scales from 20 to 200 analyses per month.

### Implementation 5: Investment Scoring Dashboard

**Price Range:** R$120,000-R$200,000
**Duration:** 2-3 months
**Prerequisites:** AVM + Legal Risk Scorer completed
**Deliverables:** Composite scoring model, map-based UI, portfolio tracking, alert configuration

**ROI:** Enables institutional-grade deal screening at individual investor cost.

## Engagement Arc (Full Journey)

```
Diagnostic      -> 1st Implementation  -> Expansion          -> Retainer
(R$35-75K)        (R$80-150K)            (R$250K-400K+)        (R$15-40K/mo)
2-3 weeks         1-2 months             3-5 months            Ongoing

Edital Parser     AVM or Aggregation     Legal Risk Scorer     Platform maintenance
& AI Readiness    Engine                 + Investment Dashboard  Data quality monitoring
Score                                    + Full Platform        New source integration
                                                                Model retraining
```

Recommended sequencing:
1. **Start** with Edital Parser (fastest ROI, proves value)
2. **Build** Aggregation Engine (foundation layer)
3. **Add** AVM + Legal Risk Scorer (intelligence layer)
4. **Deploy** Investment Dashboard (decision layer)
5. **Maintain** via retainer (continuous improvement)

## Retainer Model

**Monthly Price:** R$15,000-R$40,000
**Includes:**
- New leiloeiro source integration (ongoing as market grows)
- Data quality monitoring and scraping maintenance (sites change frequently)
- ML model retraining and accuracy monitoring
- Platform maintenance and feature enhancements
- Monthly analytics and performance reporting

**SLA:** 99.5% data freshness (daily refresh), 48-hour response for scraping breakage, monthly model accuracy review

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
