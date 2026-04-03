---
title: "Energy & Infrastructure — Sales Playbook"
type: sales-playbook
vertical: energy-infrastructure
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [energy-infrastructure, sales, hooks, objections, pricing, ICP]
---

# Energy & Infrastructure — Sales Playbook

## Ideal Client Profile (ICP)

| Attribute | Criteria |
|-----------|---------|
| **Primary ICP: Gestoras de Usinas GD** | 5--50 plants (1--5 MW each), 100--500 UCs, R$10M--R$50M revenue |
| **Secondary ICP: Integradores Solares** | R$5M--R$100M revenue, 50--500 installations/year, 10--100 employees |
| Systems Landscape | SolarZ or inverter-native monitoring + Excel billing + generic CRM or spreadsheets |
| Technology Maturity | Monitoring exists but billing/analytics manual; no consolidated portfolio view |
| Pain Indicators | Manual billing reconciliation, no fio B automation, growing inadimplencia, referral-dependent sales |
| Decision Maker | Diretor de Operacoes (gestora), Diretor Comercial (integrador), CFO (comercializadora) |
| Budget Holder | CEO/CFO; project-based budgets, no CapEx cycle dependency |
| Geography | Minas Gerais (CEMIG), Sao Paulo (Enel), Rio de Janeiro (Enel/Light), Goias (Enel), Rio Grande do Sul (CEEE/RGE) |

## Sales Hooks

### Hook 1: "Your billing reconciliation is leaking 3--8% of revenue and you can't see it in Excel."

**Context:** Use when talking to Diretor de Operacoes or CFO of any GD gestora with 100+ UCs. Billing reconciliation is the universal pain point because every gestora does it monthly.
**Supporting Data:** Manual Excel reconciliation across 200+ UCs with pre/post Marco Legal dual logic, fio B progression, and 60-month credit tracking produces 3--8% undetected errors. For a gestora with R$3M/year in GD revenue, that's R$90K--R$240K/year in leakage.
**Follow-up Question:** "How many hours does your team spend on billing reconciliation each month? When was the last time you audited distribuidora faturas for systematic errors?"

### Hook 2: "Your investors want performance reports you can't produce without weeks of manual work."

**Context:** Use with fund-backed gestoras or Investment Managers. Especially powerful during quarterly LP reporting periods.
**Supporting Data:** Most gestoras compile investor reports manually from 3+ monitoring platforms (Growatt, Huawei, SolarZ). A 30-plant portfolio report takes 2 analysts 3 weeks. Real-time performance data is unavailable. Generation variance goes unexplained.
**Follow-up Question:** "How do you consolidate generation data across different inverter brands? What's your process for explaining generation variance to investors?"

### Hook 3: "Marco Legal fio B is getting more complex every year -- and your Excel can't keep up."

**Context:** Use with any gestora or integrador managing post-2023 plants. The fio B progression (45% in 2025, 60% in 2026, 75% in 2027) creates escalating billing complexity.
**Supporting Data:** Post-Marco Legal plants require per-UC fio B calculation based on connection date, distribuidora tariff structure, and annual progression percentage. Mixed portfolios (pre and post Marco Legal) require dual calculation logic. Manual errors compound as percentages increase.
**Follow-up Question:** "How many of your plants were connected after July 2023? How are you calculating fio B for each UC? Are you confident the distribuidora is applying the correct percentage?"

### Hook 4: "Your competitors are closing deals while you're still qualifying leads by hand."

**Context:** Use with Diretor Comercial of integradores. Works especially well in competitive regions (MG, SP) where multiple integradores compete for commercial/industrial clients.
**Supporting Data:** The fastest integrador to send a proposal wins 60%+ of competitive deals. Data-driven prospecting (Google Places + CNPJ enrichment) generates 2--3x more qualified leads than referral networks alone. Conversion improves from 12% to 18% with proper lead scoring.
**Follow-up Question:** "How do you identify new commercial/industrial prospects today? How many days between first contact and proposal delivery?"

### Hook 5: "Your inadimplencia is growing faster than your portfolio -- and you're collecting reactively."

**Context:** Use with CFO or financial controller of gestoras with 200+ UCs experiencing 5--15% default rates.
**Supporting Data:** GD gestoras typically see 5--15% inadimplencia rates. Manual collection efforts start 60--90 days after default -- too late for 40% of cases. ML-based default prediction can identify at-risk UCs 30--60 days before default, enabling proactive intervention.
**Follow-up Question:** "What is your current default rate? How many days after a missed payment do you start collection efforts? Do you know which UCs are most likely to default next month?"

## Objection Handling

| Objection | Response | Evidence |
|-----------|----------|----------|
| "SolarZ already handles our monitoring" | SolarZ is excellent for generation monitoring. But who reconciles your billing? Who detects distribuidora fatura errors? Who predicts defaults? We complement SolarZ -- we even integrate their data as one of our sources. | Billing errors of 3--8% invisible to monitoring platforms |
| "We can manage this in Excel" | Excel works at 50 UCs. At 200+, with pre/post Marco Legal logic, progressive fio B, and 60-month credit tracking, errors become inevitable. Your team spends 120+ hours/month on reconciliation that a platform does in minutes. | Scale-driven error rate data |
| "Too expensive for our size" | The diagnostic is R$25K--R$60K -- less than 3 months of billing leakage. The billing platform (R$100K--R$250K) pays for itself in Year 1 with a 200--400% ROI. | Revenue leakage quantification |
| "We're building something in-house" | We deliver in 8--12 weeks using pre-built components (kiiry-dashboard, kiiry-crm, distribuidora parsers). Building in-house means learning distribuidora fatura formats, fio B calculation rules, and inverter APIs from scratch -- 6--12 months minimum. | Time-to-value: 8--12 weeks vs. 6--12 months |
| "We tried software before and it didn't work" | That's why we start with a paid diagnostic (R$25K--R$60K) that quantifies exact R$ value before building anything. You get a maturity scorecard and roadmap regardless. | Diagnostic-first methodology |

## Discovery Call Framework

### Questions to Ask

1. "Walk me through your monthly billing reconciliation -- who does it, how many UCs, how many hours?"
2. "How many of your plants are pre-Marco Legal vs. post-2023? How do you handle fio B?"
3. "Which distribuidoras do you operate with? How do you access their compensation data?"
4. "How do you monitor generation across your portfolio? Is there one dashboard or multiple platforms?"
5. "What is your current inadimplencia rate? At what point do you start collection?"
6. "How do you generate sales leads? What tools does your sales team use?"
7. "How do you produce investor or management reports? How long does it take?"
8. "Are you tracking credit balances and their 60-month expiration?"

### Red Flags (Disqualifiers)

- Fewer than 50 UCs (insufficient scale for meaningful ROI on billing platform)
- Single-plant operation (no portfolio complexity)
- No distribuidora billing responsibility (e.g., pure EPC integrador with no post-installation role)
- Active internal development team with executive backing building exact same solution
- No executive sponsorship -- inquiry driven by junior operations staff

### Green Flags (High-Fit Indicators)

- 100+ UCs with manual billing reconciliation
- Mix of pre and post Marco Legal plants (dual logic complexity)
- Operating across multiple distribuidoras (CEMIG + Enel, etc.)
- Recent investor reporting complaints or LP pressure
- Growing inadimplencia rates (5%+ and increasing)
- Sales team expressing frustration with lead quality/volume
- CFO or Diretor de Operacoes personally involved in billing reconciliation
- Recent distribuidora billing dispute that was resolved late or not at all

## Pricing Strategy

| Engagement | Price | Value Anchor | ROI Multiple |
|-----------|-------|-------------|-------------|
| Diagnostic | R$25K--R$60K | Less than 3 months of billing leakage | N/A (discovery) |
| Billing Platform | R$100K--R$250K | R$50K--R$200K/yr in recovered leakage + 1,260 hrs/yr saved | 200--400% Year 1 |
| Portfolio Dashboard | R$80K--R$200K | R$120K+/yr in prevented generation losses | 150--300% Year 1 |
| Sales CRM | R$60K--R$150K | R$1.5M--R$3M/yr in incremental revenue | 1,000--2,000% |
| Trading Intelligence | R$150K--R$350K | 5--15% procurement savings | 300--600% |
| Revenue Management | R$80K--R$200K | R$200K--R$800K/yr in default recovery | 150--400% Year 1 |
| Monthly Retainer | R$10K--R$25K/mo | Ongoing optimization + regulatory updates | Maintenance |

## Proof Points

- **Active portfolio projects**: kiiry-dashboard (solar portfolio performance) and kiiry-crm (B2B energy sales) demonstrate proven domain expertise
- **Billing error rates**: 3--8% leakage consistently found in manual reconciliation processes
- **Market growth**: GD market growing 30--40% YoY -- operational complexity outpacing manual processes
- **Regulatory complexity**: Marco Legal fio B escalation (45% in 2025, 60% in 2026) makes automation urgent
- **Technology references**: SolarZ (100K+ plants), Eleva Energia (emerging), Clarke Energia -- validates market demand
- **Lead generation impact**: Data-driven prospecting delivers 2--3x lead volume with 50% better conversion

## Competitive Positioning Statements

- vs. SolarZ: "SolarZ monitors your plants. We manage your business -- billing, performance, sales, and revenue. We integrate SolarZ data as one of our sources."
- vs. Eleva: "Eleva manages workflows. We build the analytics and intelligence layer -- forecasting, benchmarking, default prediction -- on top of operational data."
- vs. Excel: "Excel works at 50 UCs. We serve gestoras at 200+ UCs where manual processes leak 3--8% of revenue and consume 120+ hours/month."
- vs. In-house: "We deliver in 8--12 weeks with pre-built components. Building in-house means 6--12 months learning distribuidora formats and inverter APIs from scratch."

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
