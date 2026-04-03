---
title: "Real Estate — Engagement Templates"
type: engagement-templates
vertical: real-estate
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [real-estate, diagnostic, implementation, engagement, assessment]
---

# Real Estate — Engagement Templates

## Diagnostic Engagement (Paid Assessment)

**Price Range:** R$25K--R$75K
**Duration:** 2--3 weeks
**Deliverables:** Data Maturity Scorecard (7 dimensions, 1--5 scale), Current-State Architecture Diagram, Gap Analysis, Top 5 Prioritized Opportunities with ROI Projections, 12-Month Implementation Roadmap

### Week-by-Week Breakdown

#### Week 1: Systems Audit and Data Landscape

- Inventory all IT systems:
  - ERP: Sienge, UAU (TOTVS), or other
  - CRM: Vista Software, Hypnobox, CV CRM
  - Accounting: internal system, Excel, or outsourced
  - Document management: email, shared drives, or DMS
- Map data flows between land acquisition, project development, sales, and finance
- Identify siloed databases and manual handoffs (especially SPE consolidation)
- Evaluate current data sources:
  - ITBI transaction access (which municipalities?)
  - FipeZAP usage (subscription active?)
  - Cartorio RI interaction (manual or SREI/ARISP?)
  - IBGE data usage for market analysis
- Assess LGPD compliance posture for property/buyer data

#### Week 2: Process and Operational Assessment

- Review land acquisition workflow:
  - How are opportunities sourced? (networks, brokers, data?)
  - Zoning viability analysis process (manual Plano Diretor lookup?)
  - Due diligence process (matricula review, onus verification)
  - Time from identification to acquisition decision
- Assess property valuation methodology:
  - CMA process (manual comparables selection?)
  - Data sources used (ITBI, FipeZAP, listing data?)
  - Valuation accuracy benchmarks
- Evaluate SPE management (for incorporadoras):
  - Number of active SPEs
  - Patrimonio de afetacao compliance process
  - Consolidation methodology (Excel? ERP?)
  - RET tax calculation and filing
  - Investor reporting cadence and quality
- For leilao assessorias: edital screening process, valuation methodology, legal risk assessment

#### Week 3: Report and Roadmap Delivery

- Deliver Data Maturity Scorecard
- Present current-state architecture diagram
- Detail gap analysis findings
- Present top 5 prioritized opportunities with ROI projections
- Deliver 12-month implementation roadmap
- Executive presentation to leadership team

### Discovery Questions

1. How many SPEs do you currently manage? How is patrimonio de afetacao accounting handled?
2. How do you find and evaluate land acquisition opportunities today?
3. What data sources do you use for property valuation? Do you have access to ITBI transaction data?
4. How many systems does your team use daily that don't share data automatically?
5. How long does it take from land identification to purchase decision?
6. What is your current distrato rate? How do you forecast distrato risk?
7. How are investor reports generated for each SPE?
8. For leilao: how many editais do you screen per batch? What is your hit rate?
9. What is your current CRM? How does it connect to your ERP and financial systems?
10. How do you comply with LGPD for buyer/seller personal data?

### Assessment Dimensions

| Dimension | What We Measure | Scoring Criteria (1--5) |
|-----------|----------------|------------------------|
| Data Integration | Number of disconnected systems, manual data transfers | 1: All manual; 5: Fully integrated data fabric |
| Land Intelligence | Prospecting methodology, data sources, cycle time | 1: Network-only; 5: Data-driven with automated scoring |
| Valuation Maturity | AVM capability, data sources, accuracy benchmarks | 1: Manual CMA only; 5: ML-powered AVM with ITBI/FipeZAP |
| SPE Management | Consolidation automation, patrimonio de afetacao compliance | 1: Full Excel; 5: Automated multi-SPE platform |
| Sales Intelligence | CRM analytics, lead scoring, pipeline visibility | 1: Basic CRM; 5: ML-scored leads with market intelligence |
| Document Intelligence | Matricula/edital/contract processing automation | 1: All manual; 5: LLM-powered extraction and analysis |
| Regulatory Compliance | LGPD, memorial de incorporacao, DIMOB, RET | 1: Ad hoc; 5: Automated compliance with audit trail |

## Implementation Engagements

### Implementation 1: Land Intelligence Platform

**Price Range:** R$150K--R$300K
**Duration:** 8--12 weeks
**Prerequisites:** Diagnostic completed; target municipalities identified; zoning data sources confirmed

#### Phase Breakdown

- **Weeks 1--2**: Data source mapping and API/scraping strategy per target municipality (ITBI, zoning, IBGE)
- **Weeks 3--5**: Data aggregation pipeline build (ITBI transactions, FipeZAP, IBGE demographics)
- **Weeks 6--8**: Zoning viability engine (Plano Diretor rules per municipality)
- **Weeks 9--10**: Opportunity scoring model and land dossier generator
- **Weeks 11--12**: UAT, training, go-live, hypercare

### Implementation 2: Automated Valuation Engine (AVM)

**Price Range:** R$100K--R$250K
**Duration:** 8--10 weeks
**Prerequisites:** Diagnostic completed; ITBI data access confirmed for target municipalities

#### Phase Breakdown

- **Weeks 1--2**: ITBI + FipeZAP data pipeline setup; historical transaction data ingestion
- **Weeks 3--5**: Hedonic regression model development; feature engineering (location, size, age, amenities)
- **Weeks 6--7**: ABNT NBR 14653 laudo template and auto-generation
- **Weeks 8--10**: UAT, calibration, training, go-live

### Implementation 3: SPE Financial Management Platform

**Price Range:** R$200K--R$400K
**Duration:** 10--14 weeks
**Prerequisites:** Diagnostic completed; Sienge/UAU access; bank statement access for all SPEs

#### Phase Breakdown

- **Weeks 1--3**: SPE data model design; Sienge/UAU integration; bank statement ingestion setup
- **Weeks 4--7**: Patrimonio de afetacao accounting engine; NF-e matching; RET tax calculation
- **Weeks 8--10**: Consolidated dashboard; investor reporting portal; cash flow projection engine
- **Weeks 11--12**: Distrato risk model integration
- **Weeks 13--14**: UAT, training, go-live

### Implementation 4: Auction Property Intelligence

**Price Range:** R$150K--R$350K
**Duration:** 10--14 weeks
**Prerequisites:** Diagnostic completed; edital source access (CAIXA, BB, EMGEA, judicial portals)

### Implementation 5: Commercial CRM Intelligence

**Price Range:** R$80K--R$200K
**Duration:** 6--10 weeks
**Prerequisites:** Diagnostic completed; CRM API access (Vista, Hypnobox, or CV CRM)

## Engagement Arc (Full Journey)

```
Diagnostic       -> 1st Implementation  -> Expansion          -> Retainer
(R$25K--75K)        (R$100K--300K)         (R$150K--400K)        (R$10K--30K/mo)
2--3 weeks          8--12 weeks            10--14 weeks          Ongoing

Typical first-year client value: R$400K--R$1.5M+
```

**Entry point**: Land intelligence or AVM (highest urgency for incorporadoras); auction intelligence (for leilao assessorias); SPE platform (for CFO/controller pain)
**Expansion**: Add SPE management, CRM intelligence, or additional municipality coverage
**Retainer**: Ongoing platform support, model retraining, new municipality onboarding, regulatory updates

## Retainer Model

**Monthly Price:** R$10,000--R$30,000
**Includes:**
- Platform maintenance and updates
- New municipality data source onboarding (1--2 per quarter)
- ML model retraining (quarterly for AVM, monthly for lead scoring)
- 15--30 hours/month of analytics support
- ITBI data pipeline monitoring and quality checks
- Regulatory change monitoring (SREI updates, MCMV rule changes, LGPD)
**SLA:** 8-hour response for data pipeline issues, 24-hour for standard requests

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
