---
title: "Mining Consulting — Engagement Templates"
type: engagement-templates
vertical: mining
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [mining, diagnostic, implementation, engagement, assessment]
---

# Mining Consulting — Engagement Templates

## Diagnostic Engagement (Paid Assessment)

**Price Range:** R$25K--R$75K
**Duration:** 3--4 weeks
**Deliverables:** Data Maturity Scorecard (8 dimensions, 1--5 scale), Current-State Architecture Diagram, Gap Analysis, Top 5 Prioritized Opportunities with ROI Projections, 12-Month Implementation Roadmap

### Week-by-Week Breakdown

#### Week 1: Data Landscape and Systems Audit

- Inventory all IT systems:
  - ERP: TOTVS Protheus or SAP Business One
  - Mine planning: Surpac, Deswik, Vulcan, or Datamine
  - Fleet management: DISPATCH, MineStar, Wenco, or Hexagon
  - Environmental monitoring systems
  - Lab/LIMS systems
- Map data flows between geology, mine planning, production, sales, and finance
- Identify siloed databases and manual handoffs
- Evaluate ANM compliance systems:
  - RAL submission workflow
  - CFEM calculation process
  - SIGMINE/Cadastro Mineiro usage
  - PGRM platform readiness

#### Week 2: Process and Compliance Assessment

- Review all reporting workflows:
  - **ANM**: RAL, CFEM/DIEF, DIPEM
  - **Environmental**: IBAMA/SEMAD condicionantes, PRAD updates
  - **Safety**: NR-22 PGR, CIPAMIN records, incident logs
- Assess CFEM calculation methodology:
  - Current process (typically Excel spreadsheets)
  - Receita bruta calculation
  - Tax deduction logic (ICMS/PIS/COFINS)
  - Substance-specific aliquot application (1%--3.5%)
  - Error rate estimation
- Evaluate environmental license compliance:
  - LP/LI/LO condicionante tracking
  - Monitoring deadlines
  - Evidence documentation
- Review dam safety compliance under Lei 14.066/2020:
  - PAE status for all tailings dams
  - Instrumentation coverage
  - Real-time data submission to ANM

#### Week 3: Operational Efficiency Analysis

- Evaluate FMS utilization rates (benchmark: most use 30--40% of capabilities)
- Assess ore grade reconciliation processes (typically manual mine-to-mill)
- Review maintenance management:
  - Preventive vs. predictive maintenance ratio
  - Unplanned downtime frequency and cost
- Analyze energy consumption monitoring
- Assess water balance and outorga compliance

#### Week 4: Report and Roadmap Delivery

- Deliver Data Maturity Scorecard
- Present current-state architecture diagram
- Detail gap analysis findings
- Present top 5 prioritized opportunities with ROI projections
- Deliver 12-month implementation roadmap
- Executive presentation to leadership team

### Discovery Questions

1. How many systems does your team use daily that don't share data automatically?
2. How is CFEM calculated today, and who is responsible? How many hours per month?
3. How do you track environmental license condicionantes and their deadlines?
4. What percentage of your fleet management system capabilities are you actively using?
5. When was the last time geological data directly informed a production blending decision?
6. How long does RAL preparation take each year?
7. What is your dam safety monitoring process under Lei 14.066/2020?
8. How do you track NR-22 PGR requirements and CIPAMIN activities?
9. How are ESG metrics collected for reporting?
10. Have you explored BNDES financing for digital transformation?

### Assessment Dimensions

| Dimension | What We Measure | Scoring Criteria (1--5) |
|-----------|----------------|------------------------|
| Data Integration | Number of disconnected systems, manual data transfers, automated flows | 1: All manual; 5: Fully integrated data fabric |
| Reporting Automation | Time spent on regulatory and management reports | 1: 100% manual; 5: Auto-generated with human review |
| Compliance Digitization | ANM, IBAMA, SEMAD, NR-22 compliance tracking methods | 1: Paper/email; 5: Automated tracking with alerts |
| Operational Analytics | Use of FMS data, grade reconciliation, predictive models | 1: No analytics; 5: Real-time predictive dashboards |
| ESG Readiness | ESG data collection, reporting maturity, frameworks adopted | 1: Ad hoc; 5: Automated GRI/SASB/ISSB pipeline |
| Safety Analytics | NR-22 compliance, incident tracking, risk prediction | 1: Paper records; 5: Predictive safety platform |
| Geological Data Management | Drilling data, block models, production integration | 1: Siloed files; 5: Unified platform with ML models |
| Financial/CFEM Automation | CFEM calculation, tax deductions, ANM submission | 1: Full Excel; 5: Automated calculation + PGRM submission |

## Implementation Engagements

### Implementation 1: CFEM and ANM Compliance Engine

**Price Range:** R$150K--R$350K
**Duration:** 8--12 weeks
**Prerequisites:** Diagnostic completed; TOTVS Protheus or equivalent ERP with NF-e data accessible

#### Phase Breakdown

- **Weeks 1--2**: Requirements and data mapping -- NF-e data structure, substance classification, tax deduction rules
- **Weeks 3--5**: Core engine development -- extraction, calculation logic, validation rules
- **Weeks 6--8**: PGRM integration and DIEF submission automation
- **Weeks 9--10**: RAL auto-generation module
- **Weeks 11--12**: UAT, training, go-live, hypercare

### Implementation 2: Environmental Compliance Dashboard

**Price Range:** R$200K--R$500K
**Duration:** 10--14 weeks
**Prerequisites:** Diagnostic completed; inventory of all active licenses and condicionantes

#### Phase Breakdown

- **Weeks 1--3**: License document parsing and condicionante extraction
- **Weeks 4--7**: Dashboard development -- calendar, alerts, evidence management
- **Weeks 8--10**: Integration with SEMAD SLA / IBAMA Portal Ecossistemas
- **Weeks 11--12**: Dam safety module (Lei 14.066/2020 compliance)
- **Weeks 13--14**: UAT, training, go-live

### Implementation 3: Fleet and Production Analytics

**Price Range:** R$300K--R$700K
**Duration:** 12--16 weeks
**Prerequisites:** Diagnostic completed; FMS with data access (SQL/API/OPC-UA)

#### Phase Breakdown

- **Weeks 1--3**: FMS data integration and mine planning connector
- **Weeks 4--7**: Real-time dashboards (cycle times, utilization, shovel productivity)
- **Weeks 8--11**: Predictive maintenance models (OEM telemetry + FMS data)
- **Weeks 12--14**: Grade reconciliation and blending analytics
- **Weeks 15--16**: UAT, training, go-live

### Implementation 4: ESG and Safety Intelligence

**Price Range:** R$250K--R$500K
**Duration:** 12--16 weeks
**Prerequisites:** Diagnostic completed; ESG reporting requirements defined

### Implementation 5: Geological AI and Grade Optimization

**Price Range:** R$400K--R$1M
**Duration:** 16--24 weeks
**Prerequisites:** Diagnostic completed; geological database with historical drilling/assay data

## Engagement Arc (Full Journey)

```
Diagnostic       -> 1st Implementation  -> Expansion          -> Retainer
(R$25K--75K)        (R$150K--350K)         (R$200K--700K)        (R$15K--40K/mo)
3--4 weeks          8--12 weeks            10--16 weeks          Ongoing

Typical first-year client value: R$500K--R$2M+
```

**Entry point**: CFEM compliance or environmental dashboard (highest urgency, clearest ROI)
**Expansion**: Fleet analytics or geological AI (higher value, longer engagement)
**Retainer**: Ongoing platform support, model retraining, compliance updates, new regulatory integration

## Retainer Model

**Monthly Price:** R$15,000--R$40,000
**Includes:**
- Platform maintenance and updates
- Regulatory change monitoring and adaptation (ANM, IBAMA, NR-22)
- ML model retraining (quarterly)
- 20--40 hours/month of analytics support
- Priority incident response for compliance alerts
**SLA:** 4-hour response for critical compliance alerts, 24-hour for standard requests

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
