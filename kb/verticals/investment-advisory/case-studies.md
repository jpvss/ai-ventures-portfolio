---
title: "Investment Advisory — Case Studies"
type: case-studies
vertical: investment-advisory
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [investment-advisory, case-studies, outcomes, roi]
---

# Investment Advisory — Case Studies

## Case 1: Report Automation for a 20-Advisor Escritório

**Client Profile:** Mid-market escritório, ~20 advisors, R$3–5B AuC, multi-platform (XP + BTG)
**Engagement Type:** Diagnostic → Implementation (Automated Client Reporting Dashboard)
**Duration:** 2–3 weeks diagnostic + 8–12 weeks implementation
**Investment:** R$25K–R$80K diagnostic + R$150K–R$300K implementation

### Challenge

Each advisor spent 8 hours/week manually compiling client reports from multiple data sources (XP Hub, BTG portal, Gorila, spreadsheets). Total wasted time: 160 hours/week across the office. Reports were inconsistent, delayed, and lacked personalized insights. Advisors had little time remaining for client acquisition and relationship management.

### Approach

1. Deployed automated data pipeline connecting XP/BTG APIs and Gorila API into a unified data lake
2. Built AI-personalized report engine with performance attribution, benchmark comparisons, and market commentary
3. Automated delivery via email and WhatsApp Business

### Results

| Metric | Before | After | Impact |
|--------|--------|-------|--------|
| Report generation time per advisor | 8 hrs/week | 15 min/week | 97% reduction |
| Total office hours on reporting | 160 hrs/week | 5 hrs/week | 320 hrs/month redirected to revenue activities |
| FTE equivalent saved | — | 3–4 FTEs | R$30K–R$80K/month in recovered capacity |
| Report delivery consistency | Ad hoc, delayed | Automated, on-schedule | 100% on-time delivery |

### Key Learnings

- XP/BTG API access limitations required hybrid approach (API + structured data export)
- AI-generated market commentary required advisor review/approval workflow to maintain trust
- Biggest advisor satisfaction driver was the "time back" — 7+ hours/week returned to client-facing work

### Reusable Assets

- Multi-platform data normalization layer (XP + BTG + Gorila schema mapping)
- Performance attribution calculation engine
- AI report personalization prompt templates

---

## Case 2: CRM-Driven Client Acquisition

**Client Profile:** Mid-market escritório, 15–25 advisors, R$2–4B AuC
**Engagement Type:** Implementation (CRM Intelligence and Client Segmentation)
**Duration:** 6–10 weeks
**Investment:** R$100K–R$200K

### Challenge

Low and inconsistent client acquisition rates — averaging 3 new clients/month per advisor. CRM (HubSpot) was underutilized; no segmentation beyond AuC tiers. No systematic "next best action" for existing client engagement. XP's Ultra Advisors program data showed CRM-enabled offices achieving 2.5x higher captation.

### Approach

1. Unified client data layer across CRM, portfolio data, and communication history
2. AI-driven segmentation: risk profile clusters, life-stage segments, product affinity scoring
3. Automated "next best action" engine (e.g., "Client X has 60% fixed income, moderate profile, Selic is dropping → suggest rebalancing conversation")
4. Communication preference optimization

### Results

| Metric | Before | After | Impact |
|--------|--------|-------|--------|
| New clients/month per advisor | 3 | 7–8 | 2.5x increase (consistent with XP data) |
| Average AuC per new client | R$2M | R$2M | Maintained quality |
| Additional annual revenue | — | R$1.2M | 100 additional clients/year × R$2M AuC × 0.6% ROA |
| CRM adoption rate | <40% of advisors | >90% | Driven by "next best action" value |

### Key Learnings

- "Next best action" prompts were the single most valued feature — advisors adopted CRM because it told them what to do, not just stored data
- Segmentation revealed that 20% of clients generated 70% of revenue — enabled differentiated service tiers
- Integration with WhatsApp Business was essential for advisor adoption

### Reusable Assets

- Client segmentation model (risk × life-stage × product affinity)
- "Next best action" rules engine and prompt templates
- WhatsApp Business API integration pattern

---

## Case 3: Churn Reduction Through Predictive Analytics

**Client Profile:** Mid-market escritório, R$5B AuC, 30+ advisors, 12% annual churn rate
**Engagement Type:** Implementation (Churn Prediction and Client Retention Engine)
**Duration:** 8–12 weeks
**Investment:** R$120K–R$250K

### Challenge

Annual client churn of 12% on R$5B AuC meant losing R$600M in assets per year, translating to R$3.6M in lost annual revenue (at 0.6% ROA). Churn was identified only after clients left — no early warning system. Retention efforts were reactive and uncoordinated.

### Approach

1. ML model trained on behavioral signals: declining login frequency, withdrawal patterns, reduced engagement
2. External signal enrichment via Pluggy Open Finance (detecting asset movement to other institutions)
3. Early warning dashboard with 30/60/90-day risk scores
4. Automated retention playbooks triggered by risk thresholds

### Results

| Metric | Before | After | Impact |
|--------|--------|-------|--------|
| Annual churn rate | 12% | 7% | 5 percentage point reduction |
| AuC retained | — | R$250M additional | 5% × R$5B |
| Revenue retained | — | R$1.5M/year | R$250M × 0.6% ROA |
| Churn detection lead time | After departure | 30–90 days early warning | Proactive intervention |

### Key Learnings

- Withdrawal velocity (not just amount) was the strongest churn predictor
- Pluggy Open Finance data revealing asset accumulation at other institutions was a game-changer
- Retention interventions were most effective at the 60-day risk window — too early felt intrusive, too late was ineffective

### Reusable Assets

- Churn prediction ML model architecture (adaptable to different AuC scales)
- Behavioral signal extraction pipeline
- Retention playbook templates (segmented by churn risk driver)

---

## Case 4: Lead Conversion Optimization

**Client Profile:** Growing escritório, 10–20 advisors, aggressive growth targets
**Engagement Type:** Implementation (Lead Scoring and Prospecting Intelligence)
**Duration:** 6–8 weeks
**Investment:** R$80K–R$150K

### Challenge

Lead conversion rate of 5% with high time investment per lead. No systematic scoring — all leads treated equally. Advisors spent time on low-probability prospects while high-value leads went cold.

### Approach

1. AI lead scoring model integrating demographic data, social signals, estimated investable assets, and behavioral signals from marketing touchpoints
2. Automated lead prioritization and routing
3. Conversion funnel analytics

### Results

| Metric | Before | After | Impact |
|--------|--------|-------|--------|
| Lead conversion rate | 5% | 15% | 3x improvement |
| Time-to-close | Baseline | 40% reduction | Faster revenue realization |
| Additional clients/month | — | 10 additional | At R$2M avg AuC × 0.6% ROA |
| Additional annual revenue | — | R$1.44M | 120 new clients × R$2M × 0.6% |

### Key Learnings

- Estimated investable assets (derived from profession, location, social signals) was the most predictive feature
- Speed of follow-up after initial contact was the strongest controllable conversion factor
- Lead scoring reduced advisor frustration and improved morale

### Reusable Assets

- Lead scoring model architecture
- Investable asset estimation heuristics
- Marketing-to-CRM integration pipeline

---

## Quantified Outcomes Library

| Outcome Category | Metric | Typical Range | Evidence Basis |
|-----------------|--------|---------------|----------------|
| Report automation | Time savings per advisor | 6–10 hrs/week → 15–30 min/week | Project 1 outcomes |
| Advisor capacity | Clients per advisor | 100–200 → 300–500 | Combined Projects 1+2 |
| Client acquisition | New clients/month per advisor | 3 → 7–8 (2.5x) | Project 2; corroborated by XP Ultra Advisors data |
| Churn reduction | Annual churn rate | 8–15% → 4–8% | Project 4 outcomes |
| Revenue retained from churn reduction | Annual revenue saved | R$1.5M on R$5B AuC | Project 4 (5pp churn reduction × 0.6% ROA) |
| Lead conversion | Conversion rate | 5–10% → 15–25% | Project 5 outcomes |
| Lead revenue impact | Additional annual revenue | R$1.44M | 10 clients/month × R$2M AuC × 0.6% ROA |
| Compliance time savings | Compliance officer hours | 10–15 hrs/week saved | Project 3 outcomes |
| CRM-driven captation | Captation increase | 2.5x (per XP data) | XP Ultra Advisors program benchmark |
| FTE equivalent | Recovered capacity | 3–4 FTEs (R$30K–R$80K/month) | 20-advisor office, Project 1 |

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
