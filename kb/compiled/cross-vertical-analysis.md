---
title: "Cross-Vertical Analysis"
type: compiled
language: en
last_compiled: 2026-04-02
sources:
  - kb/verticals/mining/README.md
  - kb/verticals/investment-advisory/README.md
  - kb/verticals/insurance-surety/README.md
  - kb/verticals/auctions/README.md
  - kb/patterns/INDEX.md
  - kb/patterns/compliance-automation.md
  - kb/patterns/data-integration.md
  - kb/patterns/document-intelligence.md
  - kb/patterns/predictive-models.md
  - kb/patterns/alert-notification.md
  - kb/patterns/client-360.md
freshness: quarterly
tags: [cross-vertical, analysis, compiled]
---

# Cross-Vertical Analysis

## Common Engagement Patterns

All four verticals follow the same three-stage engagement arc:

| Stage | Scope | Duration | Revenue |
|-------|-------|----------|---------|
| **1. Paid Diagnostic** | Quantify waste, map systems, identify quick wins | 2--4 weeks | R$25K--R$80K |
| **2. Implementation Projects** | 2--3 projects in Year 1 (compliance, integration, AI) | 8--24 weeks each | R$150K--R$1M per project |
| **3. Retainer** | Ongoing optimization, model retraining, new features | Monthly | R$15K--R$60K/month |

### Shared engagement dynamics
- **Compliance-first entry**: Regulatory urgency bypasses IT budget cycles in every vertical
- **Data integration as foundation**: Always the first implementation -- all AI capabilities depend on unified data
- **Quantified ROI**: Every diagnostic produces specific dollar figures for waste/risk, not vague improvement promises
- **Land and expand**: Start with 1 project, expand to 2--3 within 12 months as trust builds

## Solution Reuse Matrix

| Pattern | Mining | Investment | Insurance | Auctions | Reuse Level |
|---------|:------:|:----------:|:---------:|:--------:|-------------|
| Compliance Automation | X | X | X | X | **Full** -- same 5-stage pipeline (ingest, rules, validate, alert, submit) |
| Data Integration | X | X | X | X | **Full** -- same ETL architecture, different source connectors |
| Predictive Models | X | X | X | X | **Full** -- same ML pipeline, different features/targets |
| Alert & Notification | X | X | X | X | **Full** -- same event-driven architecture, different trigger types |
| Document Intelligence | X | | X | X | **High** -- same OCR+NLP pipeline for licenses, apolices, editais |
| Client/Entity 360 | X | X | X | | **High** -- same aggregation pattern for clients, tomadores, assets |

### Specific reuse examples
- **CNPJ enrichment pipeline**: Used in LicitaLeads (insurance), LicenciaMiner (mining), CEAP (adjacent) -- directly portable
- **DuckDB/Parquet analytical layer**: Used in FloridaFlip, LicenciaMiner, CEAP, Leila do Leilao -- standardized stack
- **Multidimensional scoring engine**: Used in FloridaFlip, LicitaLeads, Leila do Leilao, Kiiry CRM, DeixaComigo -- 5 projects
- **PDF report generation**: Used in FloridaFlip, Kiiry Dashboard, LicenciaMiner, Incorporacoes Gestao -- 4 projects
- **Government data ingestion**: Used in FloridaFlip, LicitaLeads, LicenciaMiner, CEAP, Leila do Leilao -- 5 projects

## Revenue Potential by Vertical

| Vertical | Diagnostic | Implementation (Year 1) | Retainer (Annual) | 5-Client Revenue | Market Readiness |
|----------|-----------|------------------------|-------------------|------------------|------------------|
| **Insurance/Surety** | R$25K--R$75K | R$1.5M--R$3M | R$300K--R$720K | R$7.5M--R$30M | Highest urgency (sinistralidade crisis + regulatory deadlines) |
| **Mining** | R$25K--R$75K | R$500K--R$2M | R$180K--R$480K | R$2.5M--R$10M | Strong (mandatory digital CFEM + BNDES funding) |
| **Investment Advisory** | R$25K--R$80K | R$530K--R$1.25M | R$180K--R$480K | R$2.65M--R$6.25M | High (CVM 179 pressure + fee-based transition) |
| **Auctions** | R$35K--R$75K | R$800K--R$1.35M | R$180K--R$480K | R$4M--R$6.75M | Explosive growth but nascent buyer base |

## Recommended Vertical Entry Sequence

### 1. Insurance/Surety Bonds (Start now)

- **Why first**: Highest urgency (41.7% sinistralidade, Lei 15.040 deadlines), highest per-client revenue (R$1.5M--R$3M), 44 concentrated targets
- **Entry project**: Underwriting automation or SUSEP compliance
- **Portfolio proof**: LicitaLeads demonstrates government data + scoring + Lei 14.133 knowledge

### 2. Mining (Months 3--6)

- **Why second**: Mandatory digital CFEM creates forced demand, BNDES R$1B fund provides client budget, high per-engagement revenue
- **Entry project**: CFEM compliance automation
- **Portfolio proof**: LicenciaMiner demonstrates 14-source fusion + regulatory risk scoring + geospatial analysis

### 3. Investment Advisory (Months 6--9)

- **Why third**: Largest addressable market (200--400 offices), lower per-engagement revenue but higher volume, CVM 179 creating urgency
- **Entry project**: Automated reporting + Client 360
- **Portfolio proof**: FloridaFlip, Kiiry Dashboard, Incorporacoes Gestao demonstrate financial modeling + reporting + investor tools

### 4. Auctions (Months 9--12)

- **Why fourth**: Explosive growth but most fragmented buyer base, longest sales cycle to reach leiloeiros/platforms
- **Entry project**: Aggregation engine or AVM
- **Portfolio proof**: Leila do Leilao demonstrates Deal Score + ITBI cross-reference + financial simulation

## Cross-Selling Opportunities

| From Vertical | To Vertical | Cross-Sell Path |
|--------------|------------|-----------------|
| Insurance | Auctions | Seguro garantia for auction contracts; property valuation for insurance pricing |
| Mining | Insurance | ESG compliance data feeds insurance underwriting; environmental risk scoring |
| Investment | Mining | Due diligence platforms for mining investment funds; ESG monitoring for portfolios |
| Investment | Auctions | Real estate auction intelligence for investment advisory firms and FIPs |
| Auctions | Investment | Auction property portfolios as alternative investment products |
| Insurance | Mining | Surety bonds for mining contracts; environmental liability insurance |

### Cross-vertical product opportunities
- **Unified compliance platform**: Single engine serving CFEM (mining), CVM 179 (investment), SUSEP (insurance), CPC (auctions)
- **Shared CNPJ enrichment service**: One pipeline serving all 4 verticals
- **Cross-vertical alert platform**: R$200K--R$400K investment, serves all verticals via configurable rules
