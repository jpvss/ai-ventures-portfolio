---
title: "Energy & Infrastructure — Engagement Templates"
type: engagement-templates
vertical: energy-infrastructure
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [energy-infrastructure, diagnostic, implementation, engagement, assessment]
---

# Energy & Infrastructure — Engagement Templates

## Diagnostic Engagement (Paid Assessment)

**Price Range:** R$25K--R$60K
**Duration:** 2--3 weeks
**Deliverables:** Operational Maturity Scorecard (6 dimensions, 1--5 scale), Current-State Architecture Diagram, Revenue Leakage Quantification, Top 5 Prioritized Opportunities with ROI Projections, 12-Month Implementation Roadmap

### Week-by-Week Breakdown

#### Week 1: Operations and Systems Audit

- Inventory all operational systems:
  - Monitoring: SolarZ, Growatt Cloud, Huawei FusionSolar, other inverter platforms
  - Billing: Excel, Eleva Energia, custom systems
  - CRM/Sales: Genial Solar, Pipedrive, HubSpot, Excel
  - Financial: Omie, ContaAzul, TOTVS
- Map billing reconciliation workflow:
  - How are distribuidora faturas collected? (manual download, portal access)
  - How is compensation calculated per UC?
  - Pre vs. post Marco Legal plant classification
  - Fio B calculation methodology
  - Credit balance tracking process
- Assess portfolio monitoring:
  - Number of plants by inverter brand
  - Monitoring consolidation (or lack thereof)
  - Performance benchmarking methodology (if any)
  - Generation forecasting approach
- Evaluate sales/prospecting process:
  - Lead generation methods
  - Pipeline tracking
  - Quoting and proposal workflow
  - Conversion metrics

#### Week 2: Revenue Leakage and Regulatory Analysis

- Quantify billing reconciliation errors:
  - Sample 10--20% of UC faturas for discrepancies
  - Calculate error rate and annualized revenue impact
  - Identify systematic vs. random errors
- Assess inadimplencia (default) exposure:
  - Current default rate by UC segment
  - Collection process and timeline
  - Aging analysis of receivables
- Review regulatory compliance posture:
  - Marco Legal da GD transition readiness (pre/post classification)
  - Fio B calculation accuracy
  - ANEEL reporting obligations
  - LGPD compliance for UC consumer data
- Evaluate generation performance:
  - Compare actual generation vs. irradiation-adjusted expected (sample 5--10 plants)
  - Identify underperforming plants and potential causes
  - Estimate revenue impact of underdetected degradation

#### Week 3 (if needed): Report and Roadmap Delivery

- Deliver Operational Maturity Scorecard
- Present current-state architecture diagram
- Detail revenue leakage quantification (billing errors + inadimplencia + underperformance)
- Present top 5 prioritized opportunities with ROI projections
- Deliver 12-month implementation roadmap
- Executive presentation to leadership team

### Discovery Questions

1. How many UCs does your portfolio have, and how do you reconcile distribuidora faturas monthly?
2. How many hours per month does your team spend on billing reconciliation?
3. Do you have plants connected both before and after July 2023 (Marco Legal transition)?
4. How do you monitor generation performance across your portfolio? Is there a single dashboard?
5. What is your current inadimplencia rate? How do you manage collections?
6. How do you generate new sales leads? What is your current conversion rate?
7. How do you produce reports for investors or management?
8. Are you tracking credit balances and their 60-month expiration per UC?
9. Which distribuidoras do you operate with? (CEMIG, Enel, CPFL, Energisa, others)
10. Have you explored the Mercado Livre opportunity for your larger consumers?

### Assessment Dimensions

| Dimension | What We Measure | Scoring Criteria (1--5) |
|-----------|----------------|------------------------|
| Billing Automation | Fatura collection, reconciliation, dispute management | 1: Full Excel; 5: Automated reconciliation with alerts |
| Portfolio Monitoring | Generation tracking, performance benchmarking, alerting | 1: Individual inverter apps; 5: Unified dashboard with irradiation benchmark |
| Sales & Prospecting | Lead generation, pipeline management, conversion tracking | 1: Referrals only; 5: Data-driven prospecting with automated scoring |
| Revenue Management | Payment tracking, default prediction, collection workflow | 1: Manual tracking; 5: ML-based prediction with automated collection |
| Regulatory Readiness | Marco Legal compliance, fio B calculation, ANEEL reporting | 1: Unaware of changes; 5: Automated calculation with regulatory monitoring |
| Data Integration | System connectivity, data flows, single source of truth | 1: All disconnected; 5: Unified data platform with real-time feeds |

## Implementation Engagements

### Implementation 1: GD Billing & Reconciliation Platform

**Price Range:** R$100K--R$250K
**Duration:** 8--12 weeks
**Prerequisites:** Diagnostic completed; distribuidora portal access for UC faturas

#### Phase Breakdown

- **Weeks 1--2**: Requirements and data mapping -- fatura formats per distribuidora, UC portfolio structure, pre/post Marco Legal classification
- **Weeks 3--5**: Fatura parsing engine -- PDF extraction, portal scraping, field normalization
- **Weeks 6--8**: Reconciliation logic -- expected vs. actual compensation, fio B validation, credit balance tracking
- **Weeks 9--10**: Discrepancy alerting and dispute documentation generation
- **Weeks 11--12**: UAT, training, go-live, hypercare

### Implementation 2: Solar Portfolio Performance Dashboard

**Price Range:** R$80K--R$200K
**Duration:** 8--10 weeks
**Prerequisites:** Diagnostic completed; inverter monitoring platform credentials (SolarZ, Growatt, Huawei)

#### Phase Breakdown

- **Weeks 1--2**: Inverter API integration -- Growatt Cloud, Huawei FusionSolar, SolarZ connectors
- **Weeks 3--5**: Performance analytics engine -- irradiation data integration (INMET), expected generation model, performance ratio calculation
- **Weeks 6--7**: Portfolio dashboard -- unified view, plant drill-down, underperformance alerts
- **Weeks 8--9**: Investor report automation -- monthly/quarterly templates, variance analysis
- **Week 10**: UAT, training, go-live

### Implementation 3: Energy Sales CRM & Prospecting

**Price Range:** R$60K--R$150K
**Duration:** 6--10 weeks
**Prerequisites:** Diagnostic completed; target region and ICP defined

#### Phase Breakdown

- **Weeks 1--2**: Lead discovery pipeline -- Google Places API integration, CNPJ enrichment, CNAE-based estimation
- **Weeks 3--5**: Lead scoring and CRM pipeline -- scoring algorithm, energy-specific stages, proposal workflow
- **Weeks 6--8**: Dashboard and reporting -- pipeline visibility, conversion metrics, territory analysis
- **Weeks 9--10**: UAT, training, go-live

### Implementation 4: Energy Trading Intelligence

**Price Range:** R$150K--R$350K
**Duration:** 12--16 weeks
**Prerequisites:** Diagnostic completed; CCEE profile active; historical trading data available

### Implementation 5: Inadimplencia & Revenue Management

**Price Range:** R$80K--R$200K
**Duration:** 8--12 weeks
**Prerequisites:** Diagnostic completed; payment history data for 6+ months

## Engagement Arc (Full Journey)

```
Diagnostic       -> 1st Implementation  -> Expansion          -> Retainer
(R$25K--60K)        (R$80K--250K)          (R$100K--350K)        (R$10K--25K/mo)
2--3 weeks          6--12 weeks            8--16 weeks           Ongoing

Typical first-year client value: R$300K--R$1.5M
```

**Entry point**: Billing reconciliation platform (highest urgency, clearest ROI) or portfolio dashboard (for fund-backed gestoras)
**Expansion**: Trading intelligence or inadimplencia management (higher value, broader scope)
**Retainer**: Ongoing platform support, regulatory updates, ML model retraining, new distribuidora integrations

## Retainer Model

**Monthly Price:** R$10,000--R$25,000
**Includes:**
- Platform maintenance and updates
- Regulatory change monitoring and adaptation (ANEEL RENs, tariff revisions, fio B adjustments)
- ML model retraining (quarterly)
- New distribuidora portal integration as needed
- 15--30 hours/month of analytics support
- Priority incident response for billing discrepancy alerts
**SLA:** 4-hour response for critical billing alerts, 24-hour for standard requests

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
