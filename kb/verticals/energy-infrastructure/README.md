---
title: "Energy & Infrastructure — Overview"
type: README
vertical: energy-infrastructure
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [energy-infrastructure, overview, GD, solar, distributed-generation]
---

# Energy & Infrastructure Consulting (Energia & Infraestrutura)

## Summary

Brazil's distributed generation (GD) market exploded after Lei 14.300/2022 (Marco Legal da Geracao Distribuida), surpassing 2.5M consumer units (UCs), 25+ GW of installed capacity, and R$100B+ in cumulative investment. Mid-market players -- integradores solares (R$5M--R$100M revenue), gestoras de usinas GD (5--50 plants), and comercializadoras de energia -- operate with fragmented tooling: billing reconciliation across hundreds of UCs done in Excel, no consolidated performance view across solar portfolios, and generation forecasting based on guesswork rather than irradiation data.

The sector is undergoing a structural shift: the Marco Legal da GD introduced the fio B tariff (TUSD Fio B) for new GD plants post-2023, the Mercado Livre de Energia is opening to consumers above 500 kW (with progressive reduction), and ANEEL REN 1.059/2023 updated the regulatory framework for GD compensation. These changes create urgency for data infrastructure that can handle billing complexity, regulatory compliance, and portfolio optimization at scale.

JP Ventures positions itself as the AI-native data infrastructure partner for mid-market energy companies, automating the billing reconciliation, portfolio monitoring, and sales workflows that are currently manual. Our engagement model starts with a paid diagnostic (R$25K--R$60K) that quantifies operational waste, followed by implementation projects (R$60K--R$350K each) delivering 3--8x ROI within 12 months.

## Key Metrics

| Metric | Value | Source |
|--------|-------|--------|
| GD Installed Capacity (Brazil) | 25+ GW (2025) | raw/industry-templates.md |
| Number of GD Plants | 2M+ | raw/industry-templates.md |
| Consumer Units (UCs) | 2.5M+ | raw/industry-templates.md |
| Cumulative Investment | R$100B+ | raw/industry-templates.md |
| GD Market Growth (annual) | 30--40% YoY | raw/industry-templates.md |
| Avg. Diagnostic Price | R$25K--R$60K | raw/industry-templates.md |
| Implementation Range | R$60K--R$350K per project | raw/industry-templates.md |
| Target Client Revenue | R$5M--R$100M (integradores), 5--50 plants (gestoras) | raw/industry-templates.md |
| 12-Month Portfolio Value | R$300K--R$1.5M per client | raw/industry-templates.md |

## Our Positioning

JP Ventures differentiates in the energy vertical through:

1. **Billing complexity entry**: GD gestoras reconcile hundreds of faturas de energia monthly against distribuidora compensation reports. Manual errors cost 3--8% of revenue. Automation is an immediate, quantifiable win.
2. **Active portfolio projects**: kiiry-dashboard (solar portfolio performance) and kiiry-crm (B2B energy sales) give us proven domain expertise and reusable components.
3. **Regulatory transition urgency**: Marco Legal da GD transition deadlines and ANEEL REN 1.059/2023 create forcing functions for technology adoption.
4. **Mid-market focus**: We serve gestoras and integradores too large for SolarZ alone but too small for custom enterprise platforms.

## GenAI Leverage Map

### Document Intelligence (LLM)

| Document Type | Current Process | GenAI Solution | Est. ROI |
|---------------|----------------|----------------|----------|
| Faturas de energia (distribuidora bills) | Manual extraction of kWh injected, kWh compensated, TUSD/TE charges from PDF bills across hundreds of UCs | LLM parses fatura PDFs, extracts generation/consumption/compensation data, flags discrepancies against expected values | R$50K--R$200K/yr in recovered billing errors |
| Contracts with distribuidoras (CUSD/CCEAR) | Manual tracking of contract terms, tariff structures, and renewal dates in spreadsheets | LLM extracts key clauses, tariff schedules, and deadlines; structures into queryable database | Avoids missed renewal penalties |
| ANEEL regulatory documents | Manual reading and interpretation of RENs, notas tecnicas, and consultas publicas | LLM summarizes regulatory changes, identifies impact on client operations, flags compliance requirements | Proactive regulatory compliance |
| Investor reports | Manual consolidation of generation data, financial metrics, and performance benchmarks | LLM compiles data from monitoring systems, generates draft investor reports with variance analysis | 60--70% reduction in report preparation |

### Agentic Workflows

| Workflow | Steps Automated | Human-in-Loop Points | Tools Used |
|----------|----------------|---------------------|------------|
| Billing reconciliation agent | Download distribuidora compensation reports -> parse fatura data per UC -> reconcile injected vs. compensated kWh -> flag discrepancies -> generate dispute documentation | Review of flagged discrepancies before disputing with distribuidora | Distribuidora portal scraper, fatura parser, UC database, notification API |
| Performance monitoring agent | Ingest inverter data (Growatt/Huawei/SolarZ) -> compare actual vs. expected generation (irradiation-adjusted) -> identify underperforming plants -> generate maintenance alerts | Approval of maintenance dispatch; decision on warranty claims | Inverter APIs, INMET weather data, irradiation models, alert system |
| Prospecting agent | Search Google Places API for commercial/industrial establishments -> enrich with CNPJ data (Receita Federal) -> estimate energy consumption from CNAE code -> score leads -> generate outreach | Review of lead scores before outreach; approval of messaging | Google Places API, Receita Federal CNPJ API, CNAE database, CRM connector |

### Knowledge Retrieval (RAG)

| Corpus | Est. Size | Use Case | Primary Users |
|--------|-----------|----------|---------------|
| ANEEL resolutions (RENs) + notas tecnicas | ~1,500 documents | Quick lookup of GD compensation rules, tariff structures, connection requirements | Regulatory/operations team |
| Marco Legal da GD (Lei 14.300/2022) + regulamentacao | ~200 documents | Transition deadline tracking, fio B tariff rules, compensation model changes | Finance team, compliance |
| Distribuidora-specific rules (CEMIG, Enel, CPFL, Energisa) | ~500 documents per distribuidora | Regional compensation rules, connection procedures, billing formats | Operations team per region |
| CCEE market rules | ~800 documents | Free market trading rules, settlement procedures, metering standards | Comercializadoras, traders |

### Predictive Models (ML)

| Prediction | Data Available | Cold-Start Strategy | Business Impact |
|------------|---------------|---------------------|----------------|
| Generation forecasting | Inverter telemetry (kWh/h), INMET irradiation data, historical generation, weather forecasts | Start with irradiation-based linear models; layer ML as 6+ months of correlated data accumulates | 15--25% improvement in generation forecast accuracy; better financial planning |
| Demand prediction | Historical consumption data per UC, seasonal patterns, economic indicators | Begin with seasonal decomposition; train ML models after 12+ months of data | Optimized energy contracting; reduced exposure to spot market |
| Payment default prediction | Payment history, UC profile, distribuidora data, economic indicators | Rule-based scoring on payment history; ML after 6+ months of labeled data | 20--30% reduction in inadimplencia; R$200K--R$800K/yr recovered |
| Equipment degradation | Inverter performance ratios, temperature data, age, manufacturer specs | OEM degradation curves as baseline; ML refinement with actual performance data | Proactive maintenance; extended asset life |

## Decision-Maker Personas

| Persona | Key Pain Points | Hook | Buying Trigger |
|---------|----------------|------|---------------|
| Diretor de Operacoes (GD gestora) | Billing reconciliation across 100+ UCs in Excel; no consolidated portfolio view; maintenance reactive | "You're losing 3--8% of revenue to billing errors you can't see in your spreadsheets" | Portfolio growing faster than team can manage manually |
| Diretor Comercial (integrador solar) | Lead generation manual; no visibility into conversion pipeline; competitor quoting faster | "Your competitors are closing deals while you're still qualifying leads by hand" | Sales growth stalling despite market expansion |
| CFO (comercializadora) | Revenue leakage from billing mismatches; inadimplencia growing; no forecasting capability | "Your billing errors and defaults are costing more than the platform to fix them" | Cash flow pressure from growing UC portfolio |
| Investment Manager (energy fund) | No standardized performance reporting across portfolio; generation variance unexplained; due diligence manual | "Your LPs want performance data you can't produce without weeks of manual work" | LP reporting deadline or new fund raise |

## Why Now -- Urgency Signals (2025--2026)

- **Marco Legal da GD transition deadlines**: Plants connected after January 2023 subject to fio B tariff (TUSD Fio B), with progressive increase through 2028 -- billing complexity escalating rapidly
- **ANEEL REN 1.059/2023**: Updated regulatory framework for GD compensation, connection procedures, and metering -- requires system updates
- **Mercado Livre opening**: Progressive reduction of eligibility threshold (currently 500 kW, moving to all consumers by 2028) creates massive opportunity and complexity
- **GD growth acceleration**: Market growing 30--40% YoY means operational complexity outpacing manual processes
- **Distribuidora digitization**: CEMIG, Enel, CPFL moving to digital portals for compensation data -- API integration becoming feasible
- **Investor scrutiny**: Energy funds demanding standardized, real-time performance reporting across GD portfolios

## Related Portfolio Projects

- **kiiry-dashboard**: Solar portfolio performance dashboard -- real-time generation monitoring, benchmark vs. irradiation, investor reporting
- **kiiry-crm**: B2B CRM for energy sales -- lead generation using Google Places + CNPJ data, pipeline management for integradores

## File Index

| File | Description | Last Updated |
|------|-------------|-------------|
| [market-context.md](market-context.md) | Market size, players, trends, tech adoption | 2026-04-02 |
| [regulatory-map.md](regulatory-map.md) | ANEEL, ONS, CCEE, Marco Legal da GD, compensation rules | 2026-04-02 |
| [solution-patterns.md](solution-patterns.md) | 5 projects + reusable patterns, pricing | 2026-04-02 |
| [engagement-templates.md](engagement-templates.md) | 2--3 week diagnostic, assessment dimensions | 2026-04-02 |
| [competitive-intel.md](competitive-intel.md) | Landscape, differentiation, pricing intel | 2026-04-02 |
| [case-studies.md](case-studies.md) | Quantified outcomes library, ROI benchmarks | 2026-04-02 |
| [sales-playbook.md](sales-playbook.md) | 5 hooks, ICP, objection handling, pricing | 2026-04-02 |
| [tech-landscape.md](tech-landscape.md) | Systems, APIs, data sources, recommended stack | 2026-04-02 |

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
