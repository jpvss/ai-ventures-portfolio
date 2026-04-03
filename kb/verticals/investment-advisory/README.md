---
title: "Investment Advisory — Overview"
type: README
vertical: investment-advisory
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [investment-advisory, overview]
---

# Investment Advisory (Escritório de Investimento)

## Summary

Brazil's investment advisory market manages access to R$7.9 trillion in individual investment volume through ~1,384 registered firms and 26,681 certified advisors. The sector is undergoing a structural transformation driven by CVM Resolution 179 (fully effective November 2024), which mandates transparency on all commissions, pressuring advisors to demonstrate value beyond product distribution. Fee-based models are emerging — Blue3 has 20% of its base on fee-based, targeting 50%.

Mid-market escritórios (R$1–15B AuC, 10–80 advisors, 1,000–10,000+ clients) represent the sweet spot for AI consulting. These firms typically operate with 5–12 disconnected data sources, and advisors spend 6–10 hours per week on manual report generation alone. XP's own data shows that advisors using CRM properly achieve 2.5x higher client acquisition and 7x NPS improvement — yet adoption remains uneven.

JP Ventures positions itself as a data infrastructure partner that helps mid-market escritórios automate reporting, improve client retention, ensure regulatory compliance, and scale advisor capacity from 100–200 clients to 300–500 clients per advisor.

## Key Metrics

| Metric | Value | Source |
|--------|-------|--------|
| Total Investment Volume (Brazil) | R$7.9 trillion | raw/industry-templates.md |
| Registered Firms | ~1,384 | raw/industry-templates.md |
| Certified Advisors | 26,681 | raw/industry-templates.md |
| Top Firm AuC (FAMI Capital) | R$75B | raw/industry-templates.md |
| Mid-Market Sweet Spot | R$1–15B AuC, 10–80 advisors | raw/industry-templates.md |
| Typical Revenue Model | Commission 0.5–0.7% ROA | raw/industry-templates.md |
| Avg. Diagnostic Price | R$25K–R$80K | raw/industry-templates.md |
| 12-Month Portfolio Value | R$530K–R$1.25M (5 projects) | raw/industry-templates.md |

## Our Positioning

We differentiate from pure software vendors (Gorila, SmartBrain) by offering end-to-end data infrastructure consulting — not just tools, but integrated data pipelines, AI models, and compliance automation tailored to the escritório's specific tech stack and regulatory obligations. Unlike platform-provided tools (XP Hub), our solutions are platform-agnostic and work across XP, BTG, Safra, and independent platforms. Unlike in-house IT teams, we bring pre-built patterns from multiple engagements that accelerate time-to-value.

## GenAI Leverage Map

### Document Intelligence (LLM)

| Document Type | Current Process | GenAI Solution | Est. ROI |
|---------------|----------------|----------------|----------|
| Client portfolio reports | 6–10 hrs/week manual generation per advisor | Auto-generated narrative from structured portfolio data | 70–80% time reduction per advisor; reallocates ~8 hrs/week to client-facing activity |
| CVM compliance filings | Manual check against 4+ resolutions (CVM 178, 179, 30, 50) | Automated cross-reference engine that maps obligations to firm status | 90% reduction in compliance review time; near-zero missed disclosure risk |
| Client onboarding KYC documents | Manual extraction from PDFs, ID scans, proof of address | Structured data extraction with validation against CVM/ANBIMA requirements | 60–70% faster onboarding; fewer data entry errors |
| Market research summaries | Analysts reading 50+ reports/week from brokers, banks, asset managers | Auto-summarization with key signals, sentiment, and actionable highlights | 5x analyst throughput; faster reaction to market shifts |

### Agentic Workflows

| Workflow | Steps Automated | Human-in-Loop Points | Tools Used |
|----------|----------------|----------------------|------------|
| Monthly client reporting agent | Pull portfolio data → calculate performance → generate narrative → format PDF | Review narrative before send | Platform APIs (XP/BTG/Safra), LLM for narrative, PDF generation |
| CVM compliance monitoring agent | Track resolution updates → map to client obligations → flag gaps → generate action items | Approve action items before execution | CVM feed parser, obligation graph, LLM for gap analysis |
| Client rebalancing agent | Monitor drift from target allocation → identify rebalancing opportunities → generate proposal | Advisor approval before execution | Portfolio analytics engine, market data feeds, LLM for proposal narrative |
| Lead qualification agent | Ingest prospect data → score by AuC/profile → generate approach memo → assign to advisor | Advisor reviews approach memo | CRM integration, scoring model, LLM for memo generation |

### Knowledge Retrieval (RAG)

| Corpus | Est. Size | Use Case | Primary Users |
|--------|-----------|----------|---------------|
| CVM Resolutions (178, 179, 30, 50 + updates) | ~500 pages | Real-time regulatory Q&A, obligation mapping, audit preparation | Compliance officers, advisors |
| ANBIMA codes and guidelines | ~300 pages | Product suitability checks, marketing compliance, certification requirements | Compliance, marketing, advisors |
| Fund prospectuses and regulations | 1,000+ documents | Fund comparison, risk disclosure verification, client-facing fund summaries | Advisors, analysts |
| Tax rules (IR on renda fixa/variável, come-cotas) | ~200 pages | Client tax planning queries, product tax-efficiency comparison | Advisors, financial planners |
| Platform product shelf documentation (XP, BTG, Safra) | 500+ products | Product availability, fee comparison, allocation recommendations | Advisors, operations |

### Predictive Models (ML)

| Prediction | Data Available | Cold-Start Strategy | Business Impact |
|------------|---------------|---------------------|-----------------|
| Client churn prediction | Activity logs, AuC trajectory, meeting frequency, NPS responses | Rule-based heuristics (no login in 30 days, AuC decline >10%) → graduate to ML with 6 months of data | 30–60 day early warning; 15–25% churn reduction |
| Revenue per advisor optimization | Client mix, product allocation, fee vs. commission split | Benchmark against top-quartile advisors in same AuC tier | 10–20% revenue uplift per advisor through optimal client/product allocation |
| Client lifetime value | Onboarding data, first 90-day behavior, AuC growth rate | Cohort-based LTV from historical data; refine with individual features | Prioritize advisor time on highest-LTV clients; improve acquisition targeting |
| Cross-sell propensity | Portfolio composition, life stage, income bracket, risk profile | Product affinity rules (e.g., high renda fixa → introduce multimercado) → train on conversion data | 20–30% increase in products per client; higher wallet share |

## Decision-Maker Personas

### 1. Head of Operations

- **Title variants:** COO, Director of Operations, Head of Middle Office
- **Core pain:** Advisors spend 6–10 hrs/week per advisor on manual reporting. Data lives in 5–12 disconnected sources (XP, BTG, Safra portals, Excel, CRM, WhatsApp). Reconciliation is a nightmare.
- **What keeps them up:** Scaling headcount just to handle operational load; errors in client reports; advisor turnover because the job feels like data entry.
- **Hook:** "Free your advisors from Excel. They should be talking to clients, not formatting reports."
- **Budget authority:** Operational tools, data infrastructure, middleware.
- **Typical objection:** "We've tried automation before and it broke when the platform changed."

### 2. Chief Compliance Officer

- **Title variants:** CCO, Head of Compliance, Compliance Director
- **Core pain:** CVM 179 transparency mandate is fully effective. Tracking commissions across multiple platforms is manual and error-prone. Every missed disclosure is regulatory risk.
- **What keeps them up:** CVM audit findings; incomplete commission disclosure; LGPD data handling obligations.
- **Hook:** "CVM 179 is fully effective. Are you sure every commission is disclosed correctly?"
- **Budget authority:** Compliance systems, regulatory technology, audit tools.
- **Typical objection:** "Our compliance is handled by the platforms themselves."

### 3. Managing Partner

- **Title variants:** CEO, Founding Partner, Senior Partner
- **Core pain:** Advisor capacity is capped at 100–200 clients. Growing AuC means hiring more advisors, which is expensive and slow. Fee-based transition requires demonstrating value beyond product distribution.
- **What keeps them up:** Margin compression from CVM 179; losing clients to digital-first competitors; partner valuation tied to AuC growth.
- **Hook:** "Scale from 200 to 500 clients per advisor. Same team, 2.5x capacity."
- **Budget authority:** Strategic investments, technology transformation, M&A.
- **Typical objection:** "AI is overhyped. Show me a real escritório that's done this."

### 4. Head of Technology

- **Title variants:** CTO, IT Director, Head of Digital
- **Core pain:** Integrating XP, BTG, Safra APIs is a moving target. Legacy systems (Excel macros, Access databases) are fragile. Small IT team (2–5 people) is overwhelmed.
- **What keeps them up:** API breaking changes; data security; building vs. buying decisions; technical debt.
- **Hook:** "We've already built the connectors. Your team doesn't need to figure out each API."
- **Budget authority:** Technology stack, API integrations, cloud infrastructure.
- **Typical objection:** "We need to own our tech stack, not depend on a third party."

## Why Now — Urgency Signals (2025-2026)

- **CVM Resolution 179 fully effective since November 2024** — commission transparency is mandatory. Firms that haven't automated disclosure tracking are exposed to regulatory risk today.
- **Fee-based transition accelerating** — Blue3 targeting 50% fee-based, industry following. Advisors must demonstrate quantifiable value to justify fees, which requires data infrastructure.
- **Open Finance Phase 4 expanding data availability** — consent-based access to investment data creates new integration opportunities and competitive advantages for early movers.
- **Competitive pressure from digital-first firms** (Warren, Rico) forcing traditional escritórios to modernize or lose younger, digitally-native clients.
- **XP/BTG platform APIs maturing** — integration opportunities that didn't exist 18 months ago. The technical barriers to automation have dropped significantly.
- **Client expectations rising** — they compare their advisor experience to banking apps. Manual PDF reports and quarterly calls no longer meet the bar.

## Related Portfolio Projects

<!-- List projects from kb/projects/ that demonstrate capabilities in this vertical -->

## File Index

| File | Description | Last Updated |
|------|-------------|-------------|
| [market-context.md](market-context.md) | Market size, key players, tech adoption, trends | 2026-04-02 |
| [regulatory-map.md](regulatory-map.md) | CVM 178/179/30/50, ANBIMA, LGPD compliance | 2026-04-02 |
| [solution-patterns.md](solution-patterns.md) | 5 implementation projects, 6 reusable patterns, pricing | 2026-04-02 |
| [engagement-templates.md](engagement-templates.md) | 2–3 week diagnostic, discovery process, metrics | 2026-04-02 |
| [competitive-intel.md](competitive-intel.md) | Gorila, SmartBrain, Pluggy, Louro Tech, Comdinheiro | 2026-04-02 |
| [case-studies.md](case-studies.md) | Quantified outcome templates with ROI calculations | 2026-04-02 |
| [sales-playbook.md](sales-playbook.md) | 5 sales hooks, ICP, objection handling, pricing | 2026-04-02 |
| [tech-landscape.md](tech-landscape.md) | XP/BTG APIs, Open Finance, platform limitations | 2026-04-02 |

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
