---
title: "Construction — Engagement Templates"
type: engagement-templates
vertical: construction
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [construction, diagnostic, implementation, engagement, cost-control, licitacao]
---

# Construction — Engagement Templates

## Diagnostic Engagement (Paid Assessment)

**Price Range:** R$15,000-R$50,000
**Duration:** 2-3 weeks
**Deliverables:** Operations & Data Maturity Audit, Cost Control Gap Analysis, Licitacao Pipeline Assessment, 6/12/18-Month Implementation Roadmap

### Week-by-Week Breakdown

#### Week 1: Discovery & Data Mapping

| Day | Activity | Output |
|-----|----------|--------|
| 1-2 | Stakeholder interviews (Director of Engineering, Commercial Director, Financial Director) | Pain point inventory, priority ranking |
| 2-3 | System inventory: map all ERPs, spreadsheets, BIM tools, financial systems | Current-state architecture diagram |
| 3-4 | Data quality assessment: sample cost data from 3-5 active projects | Data completeness and accuracy score |
| 5 | Licitacao process walkthrough: observe current monitoring and bid preparation workflow | Process map with time/effort for each step |

#### Week 2: Analysis & Benchmarking

| Day | Activity | Output |
|-----|----------|--------|
| 1-2 | Cost control analysis: compare budget vs. actual on 5-10 recent projects | Historical variance analysis; average overrun % |
| 2-3 | SINAPI compliance audit: check 20-30 budget items against current SINAPI references | Compliance gap report; over/underpricing identification |
| 3-4 | BIM maturity assessment: evaluate current BIM usage, tools, and integration level | BIM maturity score (1-5 scale); Decreto 10.306 readiness |
| 5 | Competitive benchmarking: compare client's technology and process maturity to sector leaders | Benchmark scorecard |

#### Week 3: Roadmap & Presentation

| Day | Activity | Output |
|-----|----------|--------|
| 1-2 | Quantify value at risk: calculate annual cost of current inefficiencies | Value-at-risk model (R$ terms) |
| 3-4 | Build implementation roadmap: prioritize 3-5 projects by ROI and feasibility | 6/12/18-month roadmap with investment and expected returns |
| 5 | Executive presentation to decision-makers | Diagnostic report + roadmap deck |

### Diagnostic Deliverables

1. **Operations & Data Maturity Report** (15-20 pages)
   - Current-state architecture diagram
   - Data quality assessment across all project data sources
   - Technology adoption maturity score (1-5) across 8 dimensions
   - Identified gaps with quantified business impact

2. **Cost Control Gap Analysis** (5-10 pages)
   - Historical budget variance analysis (5-10 projects)
   - SINAPI compliance audit results
   - ABC curve analysis of cost overrun drivers
   - Estimated annual value at risk from late variance detection

3. **Licitacao Pipeline Assessment** (5-10 pages)
   - Current licitacao monitoring coverage (% of addressable market)
   - Average edital processing time and cost
   - Win/loss analysis of recent bids
   - Estimated missed opportunities (R$ pipeline value)

4. **Implementation Roadmap** (10-15 pages)
   - Prioritized project recommendations (1-5 projects)
   - Investment required and expected ROI per project
   - Timeline and resource requirements
   - Quick wins (30-60 days) vs. strategic investments (6-18 months)

### Diagnostic Conversion Strategy

The diagnostic is designed to surface quantified pain that makes implementation a no-brainer:

| Finding Type | Typical Impact | Conversion Hook |
|-------------|---------------|----------------|
| Budget overrun detected 2-3 months late | R$1-5M/year in avoidable overruns | "The Cost Control Dashboard pays for itself with one caught overrun" |
| Missing 90% of addressable licitacoes | R$10-50M in missed pipeline | "The Intelligence Radar costs R$80-200K but surfaces R$10M+ in opportunities" |
| Manual SINAPI lookup consuming 40+ hours/month | R$200-500K/year in engineer time | "Automate your most expensive manual process first" |
| Zero BIM-to-cost integration | Risk of exclusion from federal contracts | "Decreto 10.306 compliance is not optional — it's access to the market" |

## Implementation Engagement: Public Works Intelligence Radar

**Price Range:** R$80,000-R$200,000
**Duration:** 2-4 months
**Team:** 1 data engineer, 1 NLP/LLM specialist, 1 domain consultant (part-time)

### Phase 1: Data Pipeline (Weeks 1-4)

- Configure PNCP API ingestion for target regions and construction segments
- Build Diarios Oficiais scrapers for priority states (start with client's operating region)
- Set up data normalization and deduplication pipeline
- Create edital classification model (construction type, value range, qualification requirements)

### Phase 2: Intelligence Layer (Weeks 5-8)

- Deploy LLM pipeline for edital analysis: BDI extraction, technical requirements, deadlines
- Build company qualification matching engine (technical capacity, financial capacity, certifications)
- Create opportunity scoring model (fit score based on client profile and historical wins)
- Implement daily digest generation and alerting (email + WhatsApp)

### Phase 3: Dashboard & Optimization (Weeks 9-12)

- Deploy opportunity management dashboard with pipeline tracking
- Integrate bid/no-bid decision workflow
- Build historical analytics: win rate by segment, pricing analysis, competitor patterns
- Train client team on system usage and interpretation

### Success Metrics

- Coverage: monitoring 100% of PNCP publications (vs. ~5-10% manual baseline)
- Speed: edital analysis in 5 minutes (vs. 2-4 hours manual)
- Pipeline: 5-10x more qualified opportunities identified per month
- Win rate: track improvement over 6-month period (target: +10-20%)

## Implementation Engagement: Cost Control & Progress Dashboard

**Price Range:** R$100,000-R$250,000
**Duration:** 3-5 months
**Team:** 1 data engineer, 1 backend developer, 1 domain consultant (part-time)

### Phase 1: Data Integration (Weeks 1-6)

- Connect to client ERP (Sienge, TOTVS, or spreadsheet-based systems)
- Set up SINAPI automated ingestion (monthly updates)
- Build CUB index tracking by state and project type
- Create project data normalization layer (standardize across projects)

### Phase 2: Intelligence Engine (Weeks 7-12)

- Deploy SINAPI composition matching algorithm (budget items -> SINAPI codes)
- Build variance detection engine with configurable thresholds (default: 5%)
- Create ABC curve analysis automation
- Implement cash flow forecasting based on physical progress

### Phase 3: Dashboard & Alerting (Weeks 13-20)

- Deploy multi-project dashboard with drill-down by project, cost category, time period
- Configure real-time alerting (email, SMS, WhatsApp) for variance thresholds
- Build executive portfolio view: all projects consolidated
- Train project managers and cost engineers on system usage

### Success Metrics

- Variance detection: from monthly (30+ days late) to real-time (<24 hours)
- Budget accuracy: track improvement over 12 months (target: overrun reduction from 15-25% to 5-10%)
- Engineer productivity: 50%+ reduction in manual SINAPI lookup time
- Cash flow accuracy: forecast vs. actual within 5% at 30-day horizon

## Implementation Engagement: Condominium Management Platform

**Price Range:** R$60,000-R$150,000
**Duration:** 2-4 months
**Team:** 1 full-stack developer, 1 data engineer, 1 domain consultant (part-time)

### Phase 1: Financial Automation (Weeks 1-4)

- Connect bank feeds (OFX/API) for automated transaction ingestion
- Build boleto reconciliation engine across multiple condominios
- Deploy delinquency tracking with automated notification workflow
- Create financial dashboard per condominio with portfolio consolidation

### Phase 2: Operations & Communication (Weeks 5-8)

- Deploy AI chatbot for resident self-service (second via, assembleia info, maintenance requests)
- Build maintenance request management with prioritization
- Create predictive maintenance scheduling based on equipment lifecycle data
- Implement digital assembleia tools (convocacao, voting, ata generation)

### Phase 3: Optimization & Scale (Weeks 9-16)

- Deploy delinquency prediction model
- Build portfolio performance benchmarking across condominios
- Create automated compliance reporting (tax, regulatory)
- Scale onboarding process for adding new condominios rapidly

### Success Metrics

- Back-office time: 70% reduction per condominio managed
- Delinquency: 10-15% reduction through predictive intervention
- Resident satisfaction: measurable via response time (target: <2h for chatbot queries)
- Portfolio scalability: support 2-3x more buildings without proportional headcount increase

## Retainer Engagement (Post-Implementation)

**Price Range:** R$10,000-R$30,000/month
**Scope:** Ongoing optimization, model retraining, data source expansion, new feature development

| Activity | Frequency | Deliverable |
|----------|-----------|------------|
| SINAPI update integration | Monthly | Updated cost benchmarks and variance recalculation |
| Model performance review | Monthly | Accuracy metrics, retraining if needed |
| New data source integration | As needed | Expanded coverage (new states, new data providers) |
| Feature enhancements | Quarterly | New dashboard views, alerting rules, integrations |
| Quarterly business review | Quarterly | ROI validation, next-quarter priorities |

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
