---
title: "Energy & Infrastructure — Case Studies"
type: case-studies
vertical: energy-infrastructure
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [energy-infrastructure, case-studies, outcomes, roi, billing, portfolio, CRM]
---

# Energy & Infrastructure — Case Studies

## Case Study 1: Billing Reconciliation Platform for GD Gestora

**Client Profile:** GD gestora, 15 solar plants (1--3 MW each), 250 UCs across CEMIG and Enel concession areas
**Engagement Type:** Diagnostic + Implementation
**Duration:** 3 weeks diagnostic + 10 weeks implementation
**Investment:** R$35K diagnostic + R$180K implementation

### Challenge

The client reconciled distribuidora faturas manually in Excel for 250 UCs spread across two distribuidoras (CEMIG and Enel). Each month, a 3-person team spent 120+ hours downloading faturas, extracting kWh injected/compensated values, checking fio B charges for post-Marco Legal plants, and tracking credit balances. The portfolio included a mix of pre-Marco Legal (grandfathered) and post-2023 plants, requiring dual calculation logic. Undetected distribuidora errors and internal miscalculations caused an estimated 5% revenue leakage -- approximately R$180K/year.

### Approach

- Built automated fatura ingestion from CEMIG and Enel portals (PDF parsing + portal scraping)
- Developed per-UC reconciliation engine with pre/post Marco Legal dual logic
- Implemented fio B calculation with progressive percentage based on connection date
- Created 60-month credit balance tracker with expiration alerts
- Deployed discrepancy detection with configurable thresholds and automated dispute documentation

### Results

| Metric | Before | After | Impact |
|--------|--------|-------|--------|
| Billing reconciliation errors | ~5% revenue leakage | <0.5% with automated detection | R$160K+/yr recovered |
| Monthly staff hours on billing | 120 hours/month (3 people) | <15 hours/month (review only) | 1,260 hours/year freed |
| Distribuidora disputes filed | ~2/year (manually discovered) | 8--12/year (systematically detected) | Additional R$40K--R$80K recovered |
| Credit expiration risk | Untracked | 90/60/30-day alerts | Zero credits lost to expiration |

**ROI: 200--400% in Year 1**

### Key Learnings

- Distribuidora billing errors are more common than clients realize -- systematic detection finds 3--4x more than manual review
- Pre/post Marco Legal dual logic is the core complexity; most gestoras misclassify plants or miscalculate fio B
- Each distribuidora has different fatura formats, requiring distribuidora-specific parsers
- Credit balance expiration tracking (60-month window) is universally neglected

### Reusable Assets

- Fatura parsing engine (CEMIG, Enel formats)
- Pre/post Marco Legal reconciliation logic
- Credit balance tracker with expiration alerting
- Distribuidora portal scraping connectors

---

## Case Study 2: Solar Portfolio Performance Dashboard

**Client Profile:** Energy investment fund, 30 GD plants (totaling 45 MW), multiple inverter brands (Growatt, Huawei, Canadian Solar), R$200M AUM in GD assets
**Engagement Type:** Diagnostic + Implementation
**Duration:** 2 weeks diagnostic + 8 weeks implementation
**Investment:** R$25K diagnostic + R$150K implementation

### Challenge

The fund monitored 30 plants through 3 separate inverter platforms (Growatt Cloud, Huawei FusionSolar, and SolarZ for Canadian Solar inverters). No consolidated portfolio view existed. Monthly investor reports took 2 analysts 3 weeks to compile manually. Generation variance was reported as a lump number with no root cause analysis. Two plants had been underperforming by 20%+ for 6 months before anyone noticed, representing ~R$120K in lost revenue.

### Approach

- Integrated all three inverter APIs (Growatt, Huawei, SolarZ) into unified data pipeline
- Built irradiation-adjusted performance benchmarking using INMET data and NSRDB solar resource data
- Deployed portfolio-level dashboard with drill-down to plant, string, and inverter level
- Automated monthly investor report generation with variance analysis
- Implemented underperformance alerting (>10% deviation from irradiation-adjusted expected generation)

### Results

| Metric | Before | After | Impact |
|--------|--------|-------|--------|
| Report preparation time | 3 weeks (2 analysts) | 2 hours (automated + review) | ~240 hours/quarter saved |
| Underperformance detection | 6+ months lag | Real-time (<24 hours) | R$120K+/yr in prevented losses |
| Portfolio visibility | 3 separate platforms | Single unified dashboard | Executive and LP-ready |
| Generation forecast accuracy | No forecasting | ±8--12% (irradiation-adjusted) | Improved financial planning |

**Investment pays for itself within 6 months through prevented generation losses alone.**

### Key Learnings

- Inverter API quality varies significantly: Growatt API is well-documented; Huawei requires partner credentials; SolarZ provides the best aggregated data
- Irradiation-adjusted benchmarking is essential -- raw generation comparisons are meaningless without weather normalization
- Investor reports must be institutional-grade (PDF format, consistent branding, variance narratives) -- not just data dumps
- kiiry-dashboard components reduced development time by ~35%

### Reusable Assets

- Multi-inverter API integration layer (Growatt, Huawei, SolarZ)
- Irradiation-adjusted performance model (INMET/NSRDB integration)
- Investor report generation template
- Underperformance alerting engine

---

## Case Study 3: Energy Sales CRM & Prospecting for Integrador Solar

**Client Profile:** Mid-size integrador solar, R$25M revenue, 200+ installations/year, operating in Minas Gerais and Sao Paulo
**Engagement Type:** Diagnostic + Implementation
**Duration:** 2 weeks diagnostic + 8 weeks implementation
**Investment:** R$25K diagnostic + R$100K implementation

### Challenge

The integrador generated leads primarily through referrals and Instagram ads. The sales team of 8 reps tracked prospects in a shared Google Sheet. No systematic method existed to identify high-potential commercial/industrial targets. The team estimated they were reaching only 5--10% of addressable market in their operating region. Competitor integradores with faster quoting were winning deals. Conversion rate from lead to signed contract was 12%.

### Approach

- Deployed Google Places API integration to discover commercial/industrial establishments in target municipalities
- Built CNPJ enrichment pipeline (Receita Federal API) to capture razao social, CNAE code, and porte
- Developed energy consumption estimation engine using CNAE-based benchmarks and establishment size
- Implemented lead scoring algorithm combining consumption estimate, roof area potential, and competitive density
- Built pipeline dashboard with energy-specific stages (qualification, site visit, project design, proposal, connection approval, installation)

### Results

| Metric | Before | After | Impact |
|--------|--------|-------|--------|
| Qualified leads per month | 30--40 (referral-dependent) | 80--120 (data-driven + referrals) | 2--3x lead volume increase |
| Lead-to-contract conversion | 12% | 18% (higher quality leads) | 50% conversion improvement |
| Time to first contact | 3--5 days | Same day (automated scoring) | Competitive advantage on speed |
| Pipeline visibility | Google Sheets | Real-time dashboard | Management can forecast revenue |

**Estimated annual revenue impact: R$1.5M--R$3M from increased sales volume and conversion.**

### Key Learnings

- Google Places API provides excellent commercial establishment discovery but requires CNAE enrichment for energy relevance scoring
- Energy consumption estimation from CNAE code is directionally accurate (±20%) and sufficient for lead prioritization
- The fastest integrador to send a proposal wins 60%+ of competitive deals -- speed matters more than precision in quoting
- kiiry-crm components reduced development time by ~40%

### Reusable Assets

- Google Places + CNPJ enrichment pipeline
- CNAE-based energy consumption estimation engine
- Lead scoring algorithm for energy verticals
- Energy-specific CRM pipeline template

---

## Quantified Outcomes Library

| Outcome Category | Range | Basis | Evidence Strength |
|-----------------|-------|-------|-------------------|
| Billing error recovery | R$50K--R$200K/year | 3--8% leakage on 200-UC portfolio | ROI: 200--400% Year 1 |
| Staff time savings (billing) | 1,260 hours/year | 120 hrs/month -> 15 hrs/month for 250 UCs | Quantified |
| Distribuidora dispute recovery | R$40K--R$80K/year | Systematic detection finds 3--4x more errors | Quantified |
| Underperformance loss prevention | R$120K+/year | Real-time detection vs. 6-month lag | Quantified |
| Investor report automation | 240 hours/quarter | 3 weeks (2 analysts) -> 2 hours | Efficiency gain |
| Sales lead volume increase | 2--3x | Data-driven prospecting vs. referrals only | Quantified |
| Conversion rate improvement | 12% -> 18% | Higher quality leads from scoring | Quantified |
| Revenue from increased sales | R$1.5M--R$3M/year | Higher volume + better conversion | Estimated |
| Default rate reduction | 20--30% | ML-based prediction + automated collection | Projected |
| Default recovery | R$200K--R$800K/year | Proactive collection on 500-UC portfolio | Projected |
| Energy procurement savings | 5--15% | Better contracting from demand forecasting | Projected |

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
