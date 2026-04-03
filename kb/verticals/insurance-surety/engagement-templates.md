---
title: "Insurance & Surety Bonds — Engagement Templates"
type: engagement-templates
vertical: insurance-surety
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [insurance-surety, diagnostic, implementation, engagement, underwriting]
---

# Insurance & Surety Bonds — Engagement Templates

## Diagnostic Engagement (Paid Assessment)

**Price Range:** R$25,000–R$75,000
**Duration:** 2–4 weeks
**Deliverables:** Underwriting Workflow Audit, Compliance Readiness Assessment, Data Integration Maturity Report, 6/12/18-Month Implementation Roadmap

### Week-by-Week Breakdown

#### Week 1: Discovery

- **Stakeholder interviews**: CEO/COO, Head of Underwriting, IT Director, Claims Manager, Compliance Officer
- **Underwriting workflow mapping**: Map current seguro garantia workflow from tomador application through credit analysis to policy issuance
- **Technology audit**: Inventory core systems — policy admin, CRM, claims management, financial systems
- **Data source inventory**: Catalog all data sources used — credit bureaus, SUSEP data, internal databases, court records

#### Weeks 2–3: Assessment

- **Underwriting efficiency measurement**:
  - Time-to-quote
  - Time-to-issue
  - Approval rates
  - Manual vs. automated steps in the workflow
- **Claims processing benchmark**:
  - Average resolution time
  - Documentation requirements
  - Fraud detection capabilities
- **Compliance readiness evaluation**:
  - SUSEP reporting: Circular 662/2022 (seguro garantia), Circular 710/2024 (operations registration / SRO)
  - OPIN readiness: Phase 3 API capabilities
  - LGPD compliance status
  - Lei 15.040/2024 adaptation status (25-day proposal, 30-day claims deadlines)
- **Data integration maturity assessment**:
  - Number and severity of data silos
  - API capabilities of existing systems
  - Real-time data access vs. batch processing

#### Week 3–4: Analysis & Recommendations

- Gap analysis against market best practices (benchmark vs. digital leaders like Granto, Pottencial)
- Priority matrix: quick wins (<30 days) vs. strategic initiatives (3–6 months)
- ROI projections for top 3 initiatives
- 6/12/18-month implementation roadmap

### Discovery Questions

1. How many manual steps are involved in underwriting a standard seguro garantia policy?
2. What is your average time-to-issue for seguro garantia? How does this compare to your competitors?
3. How do you currently evaluate tomador credit risk? How many data sources do you cross-reference?
4. What is your current sinistralidade? How has it trended over the past 3 years?
5. How are you currently reporting to SUSEP? What percentage is automated vs. manual?
6. What is your OPIN readiness status? Do you have FAPI-certified APIs?
7. How are you adapting to Lei 15.040/2024 deadline requirements?
8. How many disconnected systems does your IT landscape include?
9. What percentage of claims involve suspected fraud? How do you detect it?
10. How do you currently manage broker relationships and data exchange?

### Assessment Dimensions

| Dimension | What We Measure | Scoring Criteria (1–5) |
|-----------|----------------|----------------------|
| Underwriting Automation | Percentage of automated steps, time-to-issue | 1=fully manual, 5=real-time automated |
| Data Integration | Number of connected systems, API maturity | 1=all siloed, 5=unified data platform |
| Compliance Digitization | SUSEP reporting automation, OPIN readiness | 1=manual spreadsheets, 5=automated real-time |
| Claims Intelligence | Fraud detection, prediction, resolution time | 1=reactive manual, 5=predictive AI-driven |
| Distribution Technology | Broker exchange, embedded insurance, digital channels | 1=phone/email only, 5=API-based real-time |
| Data Protection & Security | LGPD compliance, cybersecurity (Circular 638) | 1=no controls, 5=fully compliant + monitored |

## Implementation Engagements

### Implementation 1: Automated Underwriting Engine

**Price Range:** R$400,000–R$800,000
**Duration:** 4–6 months
**Prerequisites:** Diagnostic completed
**Deliverables:** Credit scoring ML model, document OCR pipeline, API integrations with data providers, risk dashboard

#### Phase Breakdown

1. **Data integration (Weeks 1–6)**: Connect Serasa/Boa Vista credit data, SUSEP policy history, court records (PJe, state TJ systems), B3 financial data, PNCP/ComprasNet government procurement data
2. **ML model development (Weeks 4–12)**: Train credit scoring ensemble model on historical underwriting decisions; validate against known outcomes
3. **OCR pipeline (Weeks 6–14)**: Build document intelligence for tomador applications, financial statements, editais
4. **Dashboard and integration (Weeks 12–20)**: Risk dashboard for underwriters, integration with policy admin system, approval workflow
5. **Testing and rollout (Weeks 18–24)**: Parallel run with manual process, calibration, full deployment

### Implementation 2: SUSEP Compliance Dashboard

**Price Range:** R$200,000–R$400,000
**Duration:** 3–4 months
**Prerequisites:** Diagnostic completed
**Deliverables:** Automated data extraction from policy admin, SUSEP schema validation (SRO), real-time compliance monitoring dashboard

### Implementation 3: OPIN Integration Platform

**Price Range:** R$300,000–R$600,000
**Duration:** 4–6 months
**Prerequisites:** Diagnostic completed
**Deliverables:** FAPI-certified API gateway, LGPD-compliant consent management, data sharing orchestration, competitive intelligence from shared data

### Implementation 4: Claims Intelligence & Fraud Detection

**Price Range:** R$350,000–R$700,000
**Duration:** 5–7 months
**Prerequisites:** Diagnostic completed
**Deliverables:** ML-based claims prediction, document verification (OCR + AI), fraud pattern detection, automated triage

### Implementation 5: Broker-Insurer Data Exchange Platform

**Price Range:** R$250,000–R$500,000
**Duration:** 3–5 months
**Prerequisites:** Diagnostic completed
**Deliverables:** API-based platform for real-time quote requests, policy issuance, status tracking; embedded insurance capabilities for procurement platforms

## Engagement Arc (Full Journey)

```
Diagnostic → 1st Implementation → Expansion → Retainer
(R$25–75K)   (R$200–800K)         (R$250K–700K)  (R$25–60K/mo)
```

Typical arc:
1. **Diagnostic** (2–4 weeks): Underwriting workflow audit + compliance readiness assessment
2. **1st Implementation** (3–6 months): Usually SUSEP Compliance Dashboard or Underwriting Engine (highest pain / fastest ROI)
3. **Expansion** (3–7 months): Second and third projects — Claims Intelligence, OPIN Integration, or Broker Exchange
4. **Retainer** (ongoing): System maintenance, model retraining, regulatory updates, new feature development

## Retainer Model

**Monthly Price:** R$25,000–R$60,000
**Includes:**
- ML model monitoring and retraining (quarterly or as data drift detected)
- Regulatory update implementation (SUSEP circulars, CNSP resolutions, OPIN updates)
- System performance monitoring and optimization
- Priority support for compliance and operational issues
- Monthly analytics review and optimization recommendations

**SLA:** 4-hour response for critical compliance issues, 24-hour for standard requests

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
