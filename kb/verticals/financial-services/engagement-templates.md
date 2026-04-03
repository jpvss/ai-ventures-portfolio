---
title: "Financial Services — Engagement Templates"
type: engagement-templates
vertical: financial-services
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [financial-services, engagement, diagnostic, implementation, playbook]
---

# Financial Services — Engagement Templates

## Engagement Model Overview

```
Discovery Call (Free, 30–60 min)
    ↓
Paid Diagnostic (R$20K–R$60K, 2–3 weeks)
    ↓
Implementation Project (R$80K–R$400K, 2–6 months)
    ↓
Ongoing Support / Phase 2 (R$15K–R$40K/month or new project)
```

## Phase 0: Discovery Call Framework

**Duration:** 30–60 minutes | **Cost:** Free | **Goal:** Qualify opportunity and establish credibility

### Discovery Questions

**Credit Operations:**
1. "How many credit applications do you process per month? What's your analyst-to-application ratio?"
2. "Walk me through your credit analysis process — from application to disbursement. Where are the bottlenecks?"
3. "What data sources do you use for credit scoring today? Bureau only, or do you have proprietary features?"
4. "What's your current default rate? How does that compare to your target?"

**Data Infrastructure:**
5. "How do you currently report to SCR? Manual, semi-automated, or fully automated?"
6. "Where are you on Open Finance integration? Are you a data recipient yet?"
7. "What's your core banking / loan management system? How old is it?"
8. "Do you have a data warehouse or data lake, or is data scattered across systems?"

**Strategic:**
9. "What's your 12-month growth target for portfolio origination? Can your current operations support that?"
10. "Are you raising capital soon? What story do you need to tell investors about your tech/data capabilities?"
11. "Who are your competitors gaining ground? What do they do differently with data?"

### Qualification Criteria

| Criterion | Qualified | Not Qualified |
|-----------|-----------|---------------|
| Portfolio size | R$10M+ (fintech) or R$5M+ (factoring) | Below threshold — unit economics don't work |
| Credit volume | 100+ applications/month | Below 50/month — manual process is sustainable |
| Pain urgency | Active pain (rising NPLs, scaling bottleneck, investor pressure) | "Nice to have" — will never prioritize |
| Decision maker access | CCO, CEO, or CTO in the room | Only spoke to analyst or junior staff |
| Budget | Can articulate R$100K+ investment capacity | Expects R$20K to solve everything |
| Tech baseline | Has some system (even spreadsheets); data exists somewhere | No historical data; pre-revenue startup |

## Phase 1: Paid Diagnostic

**Duration:** 2–3 weeks | **Price:** R$20K–R$60K | **Deliverable:** Diagnostic report + implementation roadmap

### Week 1: Data and Process Audit

**Day 1–2: Stakeholder Interviews**
- CCO/Head of Risk: Credit policy, scoring methodology, risk appetite, pain points
- Head of Operations: SCR reporting, collections, workflow bottlenecks
- CTO/Head of Data: Systems architecture, data sources, integration status
- Compliance: BCB reporting, LGPD, Open Finance status
- Credit analysts (2–3): Walk through actual credit analysis process end-to-end

**Day 3–4: Systems and Data Assessment**
- Map current credit workflow (application → analysis → decision → disbursement → reporting)
- Inventory all data sources (bureau, SCR, internal, Open Finance, government)
- Assess data quality: completeness, accuracy, timeliness, accessibility
- Document system architecture: core banking, CRM, bureau integrations, reporting tools
- Identify data silos and integration gaps

**Day 5: Regulatory Compliance Snapshot**
- SCR reporting process and accuracy assessment
- Open Finance integration status vs. BCB requirements
- LGPD data governance maturity
- AML/KYC process review
- e-Financeira reporting status

### Week 2: Analysis and Benchmarking

**Day 6–7: Credit Process Benchmarking**
- Time per credit decision (current vs. best-in-class)
- Cost per credit decision (analyst time + data costs + overhead)
- Default rate vs. industry benchmarks (BCB credit statistics by segment)
- Approval rate and turnaround time vs. competitors
- Fraud rate estimate vs. industry averages

**Day 8–9: Opportunity Quantification**
- Model 3 scenarios (conservative, base, aggressive) for each opportunity:
  - Credit analysis automation: time savings × analyst cost × volume
  - Improved default prediction: NPL reduction × portfolio size
  - Fraud prevention: fraud rate reduction × average fraud loss
  - Government contract origination: new leads × conversion rate × average deal size
  - Open Finance integration: enhanced scoring accuracy × portfolio impact

**Day 10: Roadmap Construction**
- Prioritize projects by ROI, feasibility, and strategic value
- Sequence projects considering dependencies (data infrastructure first)
- Estimate effort, cost, and timeline for each project
- Identify quick wins (< 4 weeks) vs. strategic initiatives (3–6 months)

### Week 3: Deliverable and Presentation

**Diagnostic Report Structure:**

1. **Executive Summary** (2 pages)
   - Current state assessment (scored 1–5 across 6 dimensions)
   - Top 3 opportunities with quantified ROI
   - Recommended roadmap (12-month)
   - Investment required vs. expected return

2. **Credit Operations Assessment** (5–8 pages)
   - Process map with bottlenecks identified
   - Time/cost per credit decision analysis
   - Default rate analysis and benchmarking
   - Scoring methodology assessment
   - Data source utilization gap analysis

3. **Technology and Data Assessment** (3–5 pages)
   - Systems architecture diagram
   - Data quality scorecard
   - Integration gap analysis
   - Open Finance readiness assessment

4. **Regulatory Compliance Assessment** (2–3 pages)
   - SCR reporting accuracy and efficiency
   - LGPD data governance maturity
   - Open Finance compliance status
   - Risk areas and remediation priorities

5. **Opportunity Analysis** (5–8 pages)
   - Per-project ROI model (3 scenarios each)
   - Implementation roadmap (sequenced, 12-month)
   - Resource requirements (internal + JP Ventures)
   - Risk factors and mitigation strategies

6. **Appendices**
   - Detailed data source inventory
   - Systems integration map
   - Benchmark data sources and methodology
   - JP Ventures team and relevant experience

### Diagnostic Pricing by Client Type

| Client Type | Diagnostic Price | Scope | Expected Implementation Pipeline |
|-------------|-----------------|-------|----------------------------------|
| Fintech de crédito (SCD/SEP) | R$30K–R$60K | Full credit ops + data + compliance | R$200K–R$600K |
| Factoring/FIDC | R$20K–R$40K | Credit ops + data audit (lighter compliance scope) | R$100K–R$350K |
| Banco digital regional | R$40K–R$60K | Full scope + legacy system assessment | R$300K–R$800K |
| Correspondente bancário (network) | R$20K–R$30K | Operations + compliance focus | R$100K–R$250K |

## Phase 2: Implementation Projects

### Project 1: Credit Risk Intelligence Platform

**Duration:** 3–5 months | **Price:** R$150K–R$350K

**Month 1: Data Infrastructure**
- Set up data lake / warehouse (Snowflake, BigQuery, or Databricks)
- Integrate bureau APIs (Serasa/SPC/Boa Vista) with rate limiting and caching
- Build SCR query automation pipeline
- Integrate Receita Federal CNPJ enrichment
- Set up PNCP government contract data feed (from licitaleads infrastructure)

**Month 2: Feature Engineering and Scoring**
- Build feature engineering pipeline (bureau, financial, behavioral, government contract features)
- Deploy rule-based scoring as baseline (go-live with v1)
- Begin ML model development (logistic regression → gradient boosting)
- Integrate Open Finance data (if consent base sufficient)

**Month 3: Credit Memo and Workflow**
- Deploy LLM-powered credit memo generator
- Build credit committee dashboard
- Implement approval/rejection workflow with audit trail
- Integrate with existing loan management system

**Month 4–5: Optimization and SCR Automation**
- Train and validate ML scoring model on historical data
- A/B test ML model vs. rule-based baseline
- Automate SCR reporting from credit decisioning pipeline
- Deploy portfolio monitoring dashboards
- Knowledge transfer and team training

**Milestones:**
- Week 4: First automated bureau queries running
- Week 8: Rule-based scoring live for new applications
- Week 12: LLM credit memo generator in production
- Week 16: ML model validated on holdout data
- Week 20: Full pipeline live; SCR automation operational

### Project 2: Government Contract Credit Origination

**Duration:** 2–4 months | **Price:** R$100K–R$250K

**Month 1: PNCP Integration and Enrichment**
- Deploy PNCP monitoring pipeline (leveraging licitaleads codebase)
- Build contractor enrichment pipeline (Receita Federal, bureau, SCR)
- Design contract-backed credit scoring methodology
- Define target contractor profiles (CNAE, contract value ranges, regions)

**Month 2: Origination Pipeline**
- Build prospect scoring and prioritization engine
- Deploy automated proposal generator (LLM-powered)
- Integrate with CRM for commercial team workflow
- Build analytics dashboard (pipeline, conversion, portfolio quality)

**Month 3–4: Optimization and Expansion**
- Tune scoring model based on early origination outcomes
- Expand monitoring to state/municipal procurement portals
- Add government entity payment reliability scoring
- Build portfolio monitoring for contract-backed loans
- Knowledge transfer and team training

### Project 3: Open Finance Data Integration

**Duration:** 3–4 months | **Price:** R$100K–R$250K

**Month 1: Consent and API Infrastructure**
- Build LGPD + Open Finance compliant consent management
- Integrate Phase 2 APIs (account data, transactions)
- Implement data quality validation and normalization
- Set up secure data storage with encryption and access controls

**Month 2: Data Processing and Feature Engineering**
- Build transaction categorization engine (income, expenses, transfers, loans)
- Develop cash flow pattern features (regularity, volatility, growth)
- Create financial health scoring from Open Finance data
- Cross-validate with bureau data for data quality assurance

**Month 3–4: Application Layer**
- Integrate Open Finance features into credit scoring pipeline
- Deploy customer financial profile dashboard
- Build cash-flow-based lending product prototype
- Validate scoring improvement on holdout data
- Knowledge transfer and documentation

## Phase 3: Ongoing Support

### Monthly Retainer Options

| Tier | Price | Scope |
|------|-------|-------|
| Basic | R$15K/month | Model monitoring, bug fixes, data source maintenance |
| Standard | R$25K/month | Basic + monthly model retraining, new feature development, regulatory updates |
| Premium | R$40K/month | Standard + dedicated engineer, new integrations, strategic advisory |

### Typical Phase 2 Expansions

After initial implementation, common follow-on projects:
- Add Fraud Detection Engine (Pattern 5) → R$150K–R$400K
- Expand to new credit products (e.g., vehicle → payroll → SME) → R$80K–R$200K per product
- Build customer-facing credit portal / app integration → R$100K–R$250K
- Implement advanced portfolio analytics and stress testing → R$80K–R$150K

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
