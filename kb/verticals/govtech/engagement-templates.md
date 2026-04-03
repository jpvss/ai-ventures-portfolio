---
title: "GovTech — Engagement Templates"
type: engagement-templates
vertical: govtech
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [govtech, diagnostic, implementation, engagement, assessment]
---

# GovTech — Engagement Templates

## Diagnostic Engagement (Paid Assessment)

**Price Range:** R$25K--R$75K
**Duration:** 2--3 weeks
**Deliverables:** Data Maturity Scorecard (6 dimensions, 1--5 scale), Current-State Data Architecture Diagram, Gap Analysis, Top 5 Prioritized Opportunities with ROI Projections, 6-Month Implementation Roadmap

### Week-by-Week Breakdown

#### Week 1: Data Landscape and Systems Audit

- Inventory all data systems and sources:
  - Procurement: PNCP integration status, ComprasNet usage, state portal access
  - Financial: SIAFI access, +Brasil/SICONV usage, budget execution systems
  - Transparency: Portal da Transparencia data, Diario Oficial publication process
  - Sanction databases: CEIS/CNEP/CEPIM access, SICAF usage, CADIN checks
  - Document management: SEI adoption, edital creation/storage workflow
- Map data flows between procurement, finance, audit, and transparency
- Identify manual processes and data gaps
- Assess API access and technical readiness:
  - PNCP API integration status
  - Internal system APIs (ERP, procurement system)
  - Data export capabilities

#### Week 2: Process and Compliance Assessment

- Review procurement workflows:
  - Edital creation and publication process
  - Supplier qualification and verification
  - Contract management and amendment tracking
  - Prestacao de contas preparation
- Assess audit/oversight processes (for TCE/Controladoria clients):
  - Current sampling methodology and coverage rate
  - Anomaly detection capabilities (manual vs. automated)
  - Report generation workflow
  - Jurisprudencia reference process
- Assess supplier intelligence processes (for private-sector clients):
  - Procurement opportunity monitoring coverage
  - Bid/no-bid decision framework
  - Qualification document management
  - Competitor analysis capabilities
- Evaluate Lei 14.133/2021 compliance status:
  - PNCP publication compliance
  - New modality adoption (dialogo competitivo)
  - Digital documentation requirements

#### Week 3: Report and Roadmap Delivery

- Deliver Data Maturity Scorecard
- Present current-state data architecture diagram
- Detail gap analysis findings with quantified impact
- Present top 5 prioritized opportunities with ROI projections
- Deliver 6-month implementation roadmap
- Executive presentation to leadership team

### Discovery Questions

1. How do you currently monitor procurement opportunities across government portals?
2. What percentage of relevant procurement notices do you estimate you're catching?
3. How long does it take to analyze a typical edital and make a bid/no-bid decision?
4. How do you verify supplier compliance (CEIS/CNEP/CADIN) -- manually or automated?
5. What is your current audit coverage rate? (for TCE/Controladoria clients)
6. How do you detect anomalies or irregularities in procurement data?
7. What is your PNCP integration status? Are you publishing/consuming PNCP data via API?
8. How do you track contract amendments (aditivos) and their compliance with original terms?
9. How is prestacao de contas prepared? How many staff-hours does it consume?
10. Have you explored AI tools like TCU's Alice/Adele for audit assistance?

### Assessment Dimensions

| Dimension | What We Measure | Scoring Criteria (1--5) |
|-----------|----------------|------------------------|
| Data Integration | Number of disconnected data sources, manual transfers, API usage | 1: All manual; 5: Fully integrated data fabric with APIs |
| Procurement Digitization | PNCP adoption, electronic procurement, digital documentation | 1: Paper-based; 5: Fully digital with PNCP integration |
| Audit/Analytics Capability | Anomaly detection, coverage rate, predictive analytics | 1: Manual sampling; 5: AI-powered 100% screening |
| Transparency Compliance | LAI compliance, open data publication, Portal da Transparencia | 1: Minimal compliance; 5: Proactive open data with dashboards |
| Supplier Intelligence | Opportunity monitoring, risk assessment, due diligence automation | 1: Manual portal checks; 5: Automated multi-source monitoring |
| Compliance Automation | CEIS/CNEP checks, SICAF management, Lei 14.133 compliance | 1: Point-in-time manual; 5: Continuous automated monitoring |

## Implementation Engagements

### Implementation 1: Procurement Intelligence Dashboard

**Price Range:** R$100K--R$250K
**Duration:** 8--12 weeks
**Prerequisites:** Diagnostic completed; PNCP API access confirmed; target procurement categories defined

#### Phase Breakdown

- **Weeks 1--2**: Requirements and data source mapping -- PNCP API, state portals, Diarios Oficiais, CATMAT/CATSER categories
- **Weeks 3--5**: Data aggregation pipeline -- multi-source ingestion, deduplication, standardization
- **Weeks 6--8**: LLM edital analysis engine and opportunity scoring model
- **Weeks 9--10**: Dashboard and alert system (real-time notifications, historical analytics)
- **Weeks 11--12**: UAT, training, go-live, hypercare

### Implementation 2: Audit Intelligence Platform

**Price Range:** R$200K--R$500K
**Duration:** 12--16 weeks
**Prerequisites:** Diagnostic completed; TCE/Controladoria sponsorship; access to procurement data (PNCP + local systems)

#### Phase Breakdown

- **Weeks 1--3**: Data ingestion from PNCP + local procurement systems + sanction databases (CEIS/CNEP/CEPIM)
- **Weeks 4--7**: Anomaly detection engine -- statistical models for price, timing, supplier network patterns
- **Weeks 8--10**: CNPJ intelligence graph -- ownership analysis, related-party detection
- **Weeks 11--13**: LLM-powered audit report generation with evidence packages
- **Weeks 14--16**: UAT with auditors, training, go-live

### Implementation 3: Transparency Dashboard

**Price Range:** R$80K--R$200K
**Duration:** 6--10 weeks
**Prerequisites:** Diagnostic completed; data source access confirmed (API keys, portal access)

#### Phase Breakdown

- **Weeks 1--2**: API integration -- Portal da Transparencia, Dados Abertos da Camara, SIAFI
- **Weeks 3--5**: Dashboard development -- spending visualization, CEAP tracker, emendas tracker
- **Weeks 6--8**: Natural language query interface and anomaly highlighting
- **Weeks 9--10**: UAT, training, public launch

### Implementation 4: Supplier Compliance Monitor

**Price Range:** R$100K--R$250K
**Duration:** 8--12 weeks
**Prerequisites:** Diagnostic completed; CNPJ list of monitored entities

### Implementation 5: Environmental Licensing Intelligence

**Price Range:** R$150K--R$350K
**Duration:** 10--14 weeks
**Prerequisites:** Diagnostic completed; target environmental agencies identified; procurement data access

## Engagement Arc (Full Journey)

```
Diagnostic       -> 1st Implementation  -> Expansion          -> Retainer
(R$25K--75K)        (R$80K--250K)          (R$150K--500K)        (R$10K--30K/mo)
2--3 weeks          6--12 weeks            10--16 weeks          Ongoing

Typical first-year client value: R$300K--R$750K
```

**Entry point (Government)**: Transparency dashboard or audit intelligence (highest visibility, clearest mandate)
**Entry point (Private)**: Procurement intelligence dashboard (immediate revenue impact)
**Expansion**: Additional projects from the 5-project menu; deeper analytics, more data sources
**Retainer**: Ongoing platform maintenance, data source monitoring, model retraining, regulatory updates

## Retainer Model

**Monthly Price:** R$10,000--R$30,000
**Includes:**
- Platform maintenance and data pipeline monitoring
- Regulatory change monitoring (Lei 14.133 implementation updates, PNCP API changes)
- ML model retraining (quarterly)
- 15--30 hours/month of analytics support
- Priority incident response for data pipeline failures
**SLA:** 4-hour response for data pipeline failures, 24-hour for standard requests

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
