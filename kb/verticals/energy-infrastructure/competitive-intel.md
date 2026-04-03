---
title: "Energy & Infrastructure — Competitive Intelligence"
type: competitive-intel
vertical: energy-infrastructure
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: monthly
tags: [energy-infrastructure, competitors, pricing, positioning, differentiation, SolarZ, Clarke, Eleva]
---

# Energy & Infrastructure — Competitive Intelligence

## Competitive Landscape

### Direct Competitors

| Competitor | Type | Focus | Pricing | Strengths | Weaknesses |
|-----------|------|-------|---------|-----------|------------|
| SolarZ | Monitoring SaaS | Plant monitoring, inverter-agnostic data aggregation | R$5--R$15/plant/month | Market leader (100K+ plants), strong brand, inverter-agnostic, mobile-first | Monitoring only -- no billing reconciliation, no CRM, no analytics layer; self-serve SaaS, not consulting |
| Eleva Energia | Operations SaaS | GD plant operations, billing management, UC portfolio | SaaS subscription (undisclosed) | Purpose-built for GD gestoras, billing workflow, UC management | Early-stage; limited analytics; no prospecting; no investor reporting |
| Genial Solar | CRM/Platform | Sales management for integradores, project pipeline | SaaS subscription | Good integrador CRM, proposal generation, project management | Integrador-only focus; no gestora/billing/monitoring capabilities |
| Clarke Energia | Marketplace | Energy marketplace, consumer-facing | Commission/transaction-based | Strong brand, consumer reach, Mercado Livre expertise | Marketplace model, not infrastructure/consulting; not B2B mid-market |
| Green Dealers | Marketplace | GD credit marketplace, remote generation | Commission/transaction-based | GD remota focus, credit trading | Narrow scope (credit marketplace only); no operational tooling |
| Solfacil | Financing | Solar financing for integradores | Financing spread | Massive distribution (largest solar lender), integrador relationships | Financing only; no operational software; complementary rather than competitive |

### Indirect Competitors (Adjacent Solutions)

| Solution | How It Competes | Our Differentiation |
|----------|----------------|---------------------|
| Growatt Cloud / Huawei FusionSolar | Free monitoring for their inverter brand | Brand-locked; no cross-brand portfolio view; no billing/analytics |
| Pipedrive / HubSpot | Generic CRM used by integradores | No energy-specific lead scoring, no CNPJ enrichment, no consumption estimation |
| Excel / Google Sheets | Billing reconciliation, payment tracking | Cannot scale beyond 50--100 UCs; error-prone; no automation |
| Accounting software (Omie, ContaAzul) | Financial tracking, invoicing | No energy-specific billing logic; no fio B calculations; no UC-level reconciliation |
| Traditional energy consultancies | Regulatory advice, project development | Advisory only -- no automated systems; no data infrastructure; manual deliverables |

## Our Differentiation

### vs. SolarZ (Monitoring SaaS)

- **Beyond monitoring**: SolarZ tracks generation; we reconcile billing, predict defaults, optimize portfolios, and generate investor reports
- **Consulting + platform**: We deliver consulting insights alongside automated systems; SolarZ is self-serve only
- **Billing reconciliation**: SolarZ has no billing/compensation reconciliation -- the highest-value pain point for gestoras
- **Complementary positioning**: We often integrate SolarZ data as one of our monitoring sources

### vs. Eleva Energia (Operations SaaS)

- **Analytics layer**: Eleva manages workflows; we build the intelligence layer (forecasting, benchmarking, default prediction)
- **Custom integration**: We connect multiple data sources (distribuidoras, inverters, INMET, CCEE); Eleva is a closed platform
- **Consulting entry**: Our diagnostic quantifies R$ value before building; Eleva is a SaaS subscription without consulting guidance
- **Investor reporting**: We generate institutional-grade investor reports; Eleva focuses on operational management

### vs. Generic CRMs (Pipedrive, HubSpot)

- **Energy-native prospecting**: We use Google Places + CNPJ + CNAE to identify and score energy leads; generic CRMs have no lead discovery
- **Consumption estimation**: We estimate energy consumption from business type and size; generic CRMs cannot
- **Energy-specific pipeline**: Our stages reflect the solar sales cycle (site visit, project design, connection approval); generic CRMs use generic stages

### vs. In-House Development

- **Pre-built components**: kiiry-dashboard and kiiry-crm reduce delivery time by 30--40% vs. building from scratch
- **Cross-client intelligence**: Patterns from multiple energy engagements (fatura parsing logic, distribuidora integrations) that in-house teams cannot replicate
- **Speed**: 6--12 weeks vs. 6--12 months for in-house development
- **Domain expertise**: We understand Marco Legal, fio B calculations, distribuidora billing formats -- in-house teams must learn from zero

## Pricing Intelligence

| Service Type | Market Range | Our Pricing | Justification |
|-------------|-------------|-------------|---------------|
| Energy diagnostic | R$30K--R$100K (consultancies) | R$25K--R$60K | Faster, quantified, leads to implementation |
| Billing platform | R$150K--R$500K (custom dev) | R$100K--R$250K | Pre-built fatura parsing; reusable components |
| Monitoring dashboard | R$100K--R$400K (custom) | R$80K--R$200K | kiiry-dashboard components reduce cost |
| Sales CRM | R$80K--R$300K (custom) | R$60K--R$150K | kiiry-crm components reduce cost |
| Trading intelligence | R$300K--R$800K (enterprise) | R$150K--R$350K | Mid-market focused; modular delivery |
| SolarZ subscription | R$5--R$15/plant/month (SaaS) | N/A (different model) | We complement SolarZ, not compete on monitoring |

## Win/Loss Patterns

### Common Win Factors

- Leading with quantified billing errors (e.g., "your 200-UC portfolio is leaking R$150K/year in reconciliation errors")
- Demonstrating Marco Legal fio B calculation expertise
- Showing kiiry-dashboard / kiiry-crm as proof of domain capability
- Offering low-risk paid diagnostic as entry point
- Connecting with Diretor de Operacoes who feels the billing pain daily

### Common Loss Factors

- Client too small (<50 UCs) -- insufficient scale for meaningful ROI
- SolarZ perceived as "good enough" (monitoring-only mindset)
- In-house developer already building a billing system
- Client unwilling to pay for diagnostic (expecting free scoping)
- Decision stuck at IT level without operational/finance executive sponsorship

### Objection Patterns

| Objection | Response | Evidence |
|-----------|----------|----------|
| "SolarZ already does what we need" | SolarZ monitors generation. Who reconciles your billing? Who detects distribuidora errors? Who predicts defaults? Monitoring is 20% of the problem. | Billing errors of 3--8% are invisible to SolarZ |
| "We can build this in Excel" | Excel works for 50 UCs. At 200+, with pre/post Marco Legal logic, fio B progression, and 60-month credit tracking, errors become inevitable. | Error rate comparison at scale |
| "Too expensive for our size" | The diagnostic is R$25K--R$60K. Your billing leakage alone is likely R$50K--R$200K/year. The platform pays for itself in months. | Revenue leakage quantification from diagnostic |
| "We're building in-house" | We deliver in 8--12 weeks using pre-built components from kiiry-dashboard/kiiry-crm. In-house takes 6--12 months and requires learning distribuidora billing formats from scratch. | Time-to-value comparison |

## Market Signals

- **SolarZ growing rapidly**: Validates market demand for GD tooling; their monitoring focus leaves billing/analytics white space
- **Eleva Energia raising capital**: Confirms VC interest in GD operations software; validates the problem space
- **Solfacil expansion**: Largest solar lender creating demand for post-installation operational tooling
- **Distribuidora digitization**: CEMIG, Enel, CPFL offering digital portals -- makes API integration feasible
- **Marco Legal fio B escalation**: Progressive complexity (45% in 2025, 60% in 2026) makes manual billing increasingly untenable
- **Mercado Livre opening**: Creates new demand for trading intelligence from existing GD players expanding into free market

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-05-02*
