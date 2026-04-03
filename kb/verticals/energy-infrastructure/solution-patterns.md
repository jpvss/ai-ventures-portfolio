---
title: "Energy & Infrastructure — Solution Patterns"
type: solution-patterns
vertical: energy-infrastructure
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [energy-infrastructure, solutions, technical, patterns, billing, portfolio, CRM, trading]
---

# Energy & Infrastructure — Solution Patterns

## Implementation Projects

| Project | Price Range | Duration | Key Deliverables |
|---------|-----------|----------|-----------------|
| GD Billing & Reconciliation Platform | R$100K--R$250K | 8--12 weeks | Automated fatura parsing, UC reconciliation, dispute generation |
| Solar Portfolio Performance Dashboard | R$80K--R$200K | 8--10 weeks | Real-time generation monitoring, irradiation benchmark, investor reports |
| Energy Sales CRM & Prospecting | R$60K--R$150K | 6--10 weeks | Google Places lead gen, CNPJ enrichment, pipeline management |
| Energy Trading Intelligence | R$150K--R$350K | 12--16 weeks | Price tracking, contract optimization, demand forecasting |
| Inadimplencia & Revenue Management | R$80K--R$200K | 8--12 weeks | Payment tracking, default prediction, collection automation |

### Project 1: GD Billing & Reconciliation Platform

**Price Range:** R$100K--R$250K
**Duration:** 8--12 weeks
**Problem:** GD gestoras managing 100--500 UCs reconcile distribuidora faturas manually in Excel. Each fatura must be checked for injected kWh, compensated kWh, fio B charges (post-Marco Legal), and credit balances. Manual errors and undetected distribuidora miscalculations cause 3--8% revenue leakage. Staff dedicate 80--120 hours/month to reconciliation for a 200-UC portfolio.
**Solution Architecture:** Automated fatura parsing (PDF/portal scraping from CEMIG, Enel, CPFL, Energisa portals), UC-level reconciliation engine with pre/post Marco Legal dual logic, discrepancy detection with configurable thresholds, automated dispute documentation generation, and credit balance tracking across the 60-month validity window.
**Key Deliverables:**
- Automated fatura ingestion from distribuidora portals
- Per-UC reconciliation with expected generation vs. compensated kWh
- Fio B calculation engine (progressive percentages per connection date)
- Discrepancy alert and dispute documentation generator
- Credit balance dashboard with expiration tracking
**ROI:** Recovers 3--8% of revenue from billing errors (R$50K--R$200K/yr for a 200-UC portfolio), eliminates 80--120 hours/month of manual reconciliation. **200--400% ROI in Year 1.**

### Project 2: Solar Portfolio Performance Dashboard

**Price Range:** R$80K--R$200K
**Duration:** 8--10 weeks
**Problem:** Gestoras and energy funds monitor plant performance through individual inverter apps (Growatt Cloud, Huawei FusionSolar, SolarZ). No consolidated portfolio view exists. Generation variance goes unexplained. Investor reports take weeks to compile manually. Underperforming plants are detected months late, after significant revenue loss.
**Solution Architecture:** Multi-source data integration from inverter APIs (Growatt, Huawei, Canadian Solar, Fronius) and SolarZ. Irradiation-adjusted performance benchmarking using INMET/NSRDB data. Portfolio-level dashboards with drill-down to plant and inverter level. Automated investor report generation with variance analysis.
**Key Deliverables:**
- Unified portfolio dashboard (all plants, all inverter brands)
- Performance ratio tracking vs. irradiation baseline
- Underperformance detection with root cause indicators
- Automated investor report generation (monthly/quarterly)
- Equipment degradation tracking and warranty alert system
**ROI:** Early detection of underperformance saves 5--15% of lost generation revenue. Investor report automation saves 40--60 hours/quarter. **Builds on kiiry-dashboard components, reducing delivery by 30--40%.**

### Project 3: Energy Sales CRM & Prospecting

**Price Range:** R$60K--R$150K
**Duration:** 6--10 weeks
**Problem:** Integradores solares generate leads through referrals and manual Google searches. No systematic prospecting identifies high-potential commercial/industrial targets. Sales pipelines are tracked in spreadsheets or generic CRMs without energy-specific workflows. Competitors with faster quoting close deals first.
**Solution Architecture:** Google Places API integration to identify commercial/industrial establishments in target regions. CNPJ enrichment via Receita Federal API (razao social, CNAE code, porte). Energy consumption estimation from CNAE code and establishment size. Lead scoring based on consumption estimate, roof area potential (satellite imagery), and competitive density. Pipeline management with energy-specific stages (site visit, project design, proposal, connection approval).
**Key Deliverables:**
- Automated lead discovery from Google Places + CNPJ data
- Energy consumption estimation engine (CNAE-based)
- Lead scoring algorithm
- Pipeline dashboard with energy-specific stages
- Proposal generation with projected savings
**ROI:** 30--50% increase in qualified leads; 20--30% improvement in conversion rate through faster quoting. **Builds on kiiry-crm components.**

### Project 4: Energy Trading Intelligence

**Price Range:** R$150K--R$350K
**Duration:** 12--16 weeks
**Problem:** Comercializadoras track Mercado Livre prices manually, manage contract portfolios in spreadsheets, and lack demand forecasting capability. CCEE settlement reconciliation is manual and error-prone. Exposure to spot market volatility (PLD -- Preco de Liquidacao de Diferencas) creates financial risk.
**Solution Architecture:** Real-time PLD tracking from CCEE data. Contract portfolio management with term/volume/price optimization. Demand forecasting using historical consumption, weather, and economic indicators. CCEE settlement reconciliation engine. Risk exposure dashboard with VaR (Value at Risk) for energy positions.
**Key Deliverables:**
- Real-time PLD and market price dashboard
- Contract portfolio optimizer (mix of long-term, short-term, spot)
- ML-based demand forecasting per consumer segment
- CCEE settlement auto-reconciliation
- Risk exposure and VaR dashboard
**ROI:** 5--15% improvement in energy procurement costs through better contracting; avoids settlement errors (R$100K--R$500K/yr). **300--600% ROI for active comercializadoras.**

### Project 5: Inadimplencia & Revenue Management

**Price Range:** R$80K--R$200K
**Duration:** 8--12 weeks
**Problem:** GD gestoras face 5--15% inadimplencia (default) rates across their UC portfolio. Payment tracking is manual. Collection efforts are reactive, not risk-based. No prediction of which UCs are likely to default. Revenue forecasting is unreliable.
**Solution Architecture:** Centralized payment tracking per UC with distribuidora and direct billing data. Default prediction model using payment history, UC profile (residential/commercial/industrial), consumption patterns, and economic indicators. Automated collection workflow with escalation tiers. Revenue forecasting dashboard.
**Key Deliverables:**
- UC-level payment tracking dashboard
- ML-based default prediction scoring
- Automated collection workflow (SMS/email/WhatsApp escalation)
- Revenue forecasting with risk-adjusted projections
- Aging report and cash flow dashboard
**ROI:** 20--30% reduction in default rates; R$200K--R$800K/yr recovered for a 500-UC portfolio. **150--400% ROI in Year 1.**

## Reusable Solution Patterns

### Pattern 1: Fatura Parsing Engine

**Pipeline:** Distribuidora PDF/portal download -> OCR/structured extraction -> field normalization (kWh injected, kWh compensated, TUSD, TE, fio B) -> UC database matching -> reconciliation logic
**Cross-Vertical Applicability:** Invoice/document parsing applicable to any billing-intensive industry.

### Pattern 2: Multi-Source Inverter Integration

**Pipeline:** Growatt Cloud API + Huawei FusionSolar API + SolarZ API + other manufacturers -> normalized generation data -> time-series database -> performance analytics
**Cross-Vertical Applicability:** IoT device data aggregation pattern for any multi-vendor monitoring scenario.

### Pattern 3: Irradiation-Adjusted Performance Benchmark

**Pipeline:** INMET/NSRDB irradiation data + plant specs (capacity, orientation, tilt) -> expected generation model -> actual vs. expected comparison -> performance ratio calculation -> underperformance alerts
**Cross-Vertical Applicability:** Any asset performance monitoring against environmental conditions.

### Pattern 4: CNPJ-Enriched Lead Scoring

**Pipeline:** Google Places API (establishment discovery) -> Receita Federal CNPJ API (company data) -> CNAE-based consumption estimation -> satellite roof area analysis -> lead score -> CRM injection
**Cross-Vertical Applicability:** B2B prospecting in any vertical targeting commercial/industrial establishments.

### Pattern 5: Payment Default Prediction

**Pipeline:** Payment history + UC profile + consumption data + economic indicators -> feature engineering -> ML classification (default/no-default) -> risk scoring -> collection prioritization
**Cross-Vertical Applicability:** Inadimplencia prediction for any subscription/recurring billing business.

## Technology Recommendations

See [tech-landscape.md](tech-landscape.md) for the full recommended stack. Key choices:
- **Cloud**: AWS (cost-effective for startups) or GCP (strong ML tooling)
- **Data Platform**: PostgreSQL + TimescaleDB for time-series generation data
- **Visualization**: Metabase or custom React dashboards
- **ML**: Python (scikit-learn, LightGBM) for prediction models
- **Integration**: Python scrapers + API connectors for distribuidora/inverter data

## Data Architecture

Typical data flow for energy implementations:

```
Source Systems                  Integration Layer              Analytics Layer
-----------------              -----------------              ---------------
Growatt Cloud API          --> Python ingestion pipeline  --> PostgreSQL + TimescaleDB
Huawei FusionSolar API         (scheduled jobs)               (structured + time-series)
SolarZ API                                                         |
Distribuidora portals      --> PDF parser / scraper      --> Metabase / React dashboards
INMET irradiation data                                     --> ML models (forecasting)
Google Places API          --> Lead enrichment pipeline   --> CRM / pipeline management
CCEE data                  --> Settlement reconciliation  --> Alert/notification system
```

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
