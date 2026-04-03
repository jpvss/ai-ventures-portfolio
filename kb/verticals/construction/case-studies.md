---
title: "Construction — Case Studies"
type: case-studies
vertical: construction
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [construction, case-studies, outcomes, roi, cost-control, licitacao]
---

# Construction — Case Studies

## Case 1: Mid-Market Construtora — Cost Control & Licitacao Intelligence

**Client Profile:** Regional construtora, R$80M annual revenue, 12-15 simultaneous projects (mix of public works and private commercial), 150 employees
**Engagement Type:** Diagnostic (3 weeks) + Implementation (Cost Control Dashboard + Public Works Radar)
**Duration:** 7 months total (3 weeks diagnostic + 6 months implementation)
**Investment:** R$35K diagnostic + R$220K implementation = R$255K total

### Situation

The construtora was experiencing consistent budget overruns averaging 18% across public works projects. Cost engineers spent ~40 hours/month on manual SINAPI lookups for budget preparation. The commercial team monitored licitacoes in only 3 of the 15 municipalities within their operating region, using manual Diario Oficial searches. They estimated missing 70-80% of relevant opportunities.

Financial data was managed in 8 separate spreadsheets (one per project manager), consolidated manually by the financial director every 45 days. By the time overruns were identified, corrective action was limited to renegotiation or margin compression.

### Diagnostic Findings

| Finding | Quantified Impact |
|---------|------------------|
| Average budget overrun across 10 recent projects | 18.3% (R$14.6M on R$80M portfolio) |
| SINAPI compliance gaps (overpriced items in public works budgets) | 12% of budget items priced >15% above SINAPI reference |
| Manual SINAPI lookup time (cost engineering team) | 480 hours/year = R$288K in engineer time |
| Licitacao coverage (municipalities monitored vs. addressable) | 3 of 15 municipalities = 20% coverage |
| Estimated missed licitacao pipeline (based on PNCP data) | R$45M in annual contract value not being bid |
| Data consolidation lag (budget vs. actual comparison) | 45 days average; some projects 60+ days |

### Implementation

**Phase 1 — Cost Control Dashboard (Months 1-4):**
- Connected Sienge ERP data feeds for all 12 active projects
- Built automated SINAPI composition matching (budget items -> SINAPI codes)
- Deployed variance detection engine with 5% threshold and SMS/WhatsApp alerting
- Created multi-project executive dashboard with ABC curve analysis
- Automated monthly SINAPI update ingestion and variance recalculation

**Phase 2 — Public Works Intelligence Radar (Months 3-6, overlapping):**
- Configured PNCP API ingestion for all 15 target municipalities + 30 additional high-opportunity municipalities
- Built Diarios Oficiais scrapers for the client's state
- Deployed LLM pipeline for edital analysis: BDI extraction, qualification matching, deadline tracking
- Created daily opportunity digest with fit scoring
- Built bid pipeline dashboard with win/loss tracking

### Results (Measured at 6 Months Post-Implementation)

| Metric | Before | After | Improvement |
|--------|--------|-------|-------------|
| Average budget overrun | 18.3% | 7.2% | -11.1 percentage points |
| Variance detection time | 45 days | <24 hours | 98% faster |
| SINAPI lookup time (monthly) | 40 hours | 4 hours | -90% |
| Municipalities monitored | 3 | 45 | 15x coverage |
| Qualified opportunities identified (monthly) | 3-5 | 25-35 | 7x more |
| Edital analysis time | 2-4 hours | 5 minutes | 30-50x faster |
| Estimated annualized savings (overrun reduction) | — | R$8.8M | On R$80M portfolio |
| New pipeline from expanded monitoring | — | R$12M in first 6 months | Previously invisible opportunities |

**ROI:** R$255K investment, R$8.8M+ in annualized savings from overrun reduction alone = 34x ROI. The expanded licitacao pipeline added R$12M in addressable opportunities within 6 months.

### Key Learnings

1. **Data quality was better than expected**: Despite operating on spreadsheets, the client had years of project cost data that became highly valuable once consolidated and benchmarked against SINAPI
2. **Behavioral change was the hardest part**: Project managers initially resisted real-time cost visibility, viewing it as surveillance. Framing it as "early warning that protects your project" shifted adoption
3. **Quick win drove buy-in**: The first variance alert caught a R$340K overrun on a subcontractor contract at week 3 of the dashboard going live — this single catch covered the diagnostic cost

## Case 2: Administradora de Condominios — Operations Automation

**Client Profile:** Administradora managing 85 condominios (residential and commercial), R$12M annual revenue, 35 employees
**Engagement Type:** Diagnostic (2 weeks) + Implementation (Condominium Management Platform)
**Duration:** 4.5 months total
**Investment:** R$18K diagnostic + R$95K implementation = R$113K total

### Situation

The administradora was growing rapidly (from 50 to 85 condominios in 18 months) but back-office headcount had nearly doubled (from 18 to 35 employees). Each new condominio required approximately 0.4 FTE in back-office support for financial reconciliation, delinquency management, resident communication, and compliance. The owner wanted to reach 150 condominios without proportionally growing the team.

Financial reconciliation across 85 bank accounts (one per condominio) consumed 3 FTEs. Delinquency averaged 12.5% across the portfolio. Resident inquiries (second via, assembleia dates, maintenance status) were handled by phone, with average response time of 8-12 hours.

### Diagnostic Findings

| Finding | Quantified Impact |
|---------|------------------|
| Back-office FTE per condominio | 0.41 FTE (vs. industry benchmark 0.15-0.20) |
| Financial reconciliation labor | 3 FTEs = R$252K/year |
| Average delinquency rate | 12.5% = R$1.8M in outstanding receivables |
| Resident inquiry response time | 8-12 hours average |
| Monthly compliance report preparation | 40 hours/month across all condominios |
| Growth ceiling at current staffing | ~95 condominios before service quality degrades |

### Implementation

**Phase 1 — Financial Automation (Weeks 1-6):**
- Connected 85 bank accounts via OFX/API for automated transaction ingestion
- Built boleto reconciliation engine with automated matching and exception handling
- Deployed delinquency dashboard with automated notification workflows (SMS, email, WhatsApp)
- Created portfolio-level financial consolidation with per-condominio drill-down

**Phase 2 — Communication & Operations (Weeks 7-12):**
- Deployed AI chatbot (WhatsApp-based) for resident self-service: second via, assembleia info, maintenance requests, financial statements
- Built maintenance request management system with prioritization and tracking
- Created digital assembleia tools: automated convocacao, voting management, ata generation
- Deployed compliance report automation

**Phase 3 — Predictive Analytics (Weeks 13-18):**
- Trained delinquency prediction model on 2 years of payment history
- Built predictive maintenance scheduling based on equipment age and failure history
- Created portfolio benchmarking dashboard (cost per unit, delinquency rate, satisfaction proxy)

### Results (Measured at 6 Months Post-Implementation)

| Metric | Before | After | Improvement |
|--------|--------|-------|-------------|
| Back-office FTE per condominio | 0.41 | 0.14 | -66% |
| Financial reconciliation labor | 3 FTEs | 0.5 FTE | -83% |
| Delinquency rate | 12.5% | 8.2% | -4.3 percentage points |
| Resident inquiry response time | 8-12 hours | <15 minutes (chatbot), <2 hours (human) | 95%+ faster |
| Monthly compliance preparation | 40 hours | 6 hours | -85% |
| Portfolio capacity (same team) | ~95 condominios | 200+ condominios | 2x+ capacity |
| Condominios added post-implementation | — | 28 (in 6 months) | Growth unblocked |

**ROI:** R$113K investment. Labor savings: R$420K/year (reduced 8.5 FTEs equivalent). Delinquency recovery improvement: R$780K in recovered receivables over 6 months. Total first-year return: R$1.2M+ = 10.6x ROI.

### Key Learnings

1. **WhatsApp chatbot was the adoption catalyst**: Residents loved the instant response; syndics (sindicos) reported dramatically fewer complaints; this became the "selling point" for new condominio acquisition
2. **Delinquency prediction drove proactive intervention**: The ML model identified residents likely to default 30-60 days before payment was due, enabling friendly reminders that prevented delinquency rather than chasing it
3. **Scale economics are dramatic**: The marginal cost of adding a new condominio dropped from ~R$3K/month (0.4 FTE) to ~R$500/month (data onboarding only), fundamentally changing the growth economics

## Case 3: Public Works Construtora — Compliance & BIM Integration

**Client Profile:** Construtora specializing in public infrastructure (roads, bridges, sanitation), R$150M annual revenue, 300 employees, operating across 3 states
**Engagement Type:** Implementation (Compliance Tracker + BIM Data Integration pilot)
**Duration:** 8 months
**Investment:** R$140K (Compliance Tracker) + R$180K (BIM Integration pilot) = R$320K total

### Situation

The construtora had received R$380K in NR-18 fines in the previous 12 months across 8 active construction sites. Environmental license renewals had been missed twice, resulting in temporary project shutdowns (15 and 22 days respectively, costing an estimated R$1.2M in delays). BIM was required for a new R$45M DNIT bridge contract, but the firm had no BIM-to-cost integration — engineers were manually transcribing quantities from Revit models to SICRO-based spreadsheets.

### Results (Measured at 6 Months Post-Implementation)

| Metric | Before | After | Improvement |
|--------|--------|-------|-------------|
| NR-18 fines (annual) | R$380K | R$25K | -93% |
| Missed permit renewals | 2 in 12 months | 0 in 6 months | 100% compliance |
| Project shutdown days (permit-related) | 37 days | 0 days | Eliminated |
| BIM quantity takeoff time (per project) | 2-3 weeks | 2-3 days | 80-85% faster |
| SICRO composition matching accuracy | ~85% (manual) | 94% (automated) | +9 percentage points |
| Compliance documentation preparation | 60 hours/month | 10 hours/month | -83% |

**ROI:** R$320K investment. NR-18 fine reduction: R$355K/year. Eliminated shutdown costs: R$1.2M+ avoided. BIM efficiency: R$200K+/year in engineer time. Total first-year return: R$1.75M+ = 5.5x ROI.

### Key Learnings

1. **Computer vision for PPE detection was a force multiplier**: Safety managers could monitor 8 sites from a central dashboard; the AI flagged PPE non-compliance in real-time photos uploaded by site supervisors
2. **BIM-to-SICRO mapping required significant domain expertise**: The ML model needed extensive training data mapping IFC elements to SICRO compositions; initial accuracy was 78%, improved to 94% after 3 months of supervised learning with the client's cost engineers
3. **The compliance tracker became a differentiator in licitacoes**: The construtora started including their compliance management system in bid proposals as evidence of operational maturity, which contributed to winning 2 competitive bids where compliance track record was an evaluation criterion

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
