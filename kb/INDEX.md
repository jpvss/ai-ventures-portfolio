---
title: "JP Ventures — Consulting Knowledge Base"
type: index
vertical: cross-vertical
language: en
last_compiled: 2026-04-02
sources: [raw/agency-setup.md, raw/industry-templates.md]
freshness: monthly
tags: [index, navigation, master]
---

# JP Ventures — Consulting Knowledge Base

> LLM-maintained knowledge system for JP Ventures consulting operations.
> Last compiled: 2026-04-02 | Verticals: 11 | Projects: 10 | Patterns: 6

---

## Quick Navigation

| I need to...                          | Go to                                          |
|---------------------------------------|-------------------------------------------------|
| Understand a vertical market          | `kb/verticals/{name}/README.md`                |
| Find a reusable technical pattern     | `kb/patterns/INDEX.md`                         |
| Review project learnings              | `kb/projects/{slug}/README.md`                 |
| Check agency positioning              | `kb/agency/positioning.md`                     |
| Get pricing guidance                  | `kb/agency/pricing-framework.md`               |
| Find regulatory requirements          | `kb/verticals/{name}/regulatory-map.md`        |
| Prepare for a sales conversation      | `kb/verticals/{name}/sales-playbook.md`        |
| See engagement templates              | `kb/verticals/{name}/engagement-templates.md`  |
| Review delivery methodology           | `kb/agency/delivery-process.md`                |
| Check tech stack decisions            | `kb/agency/tech-stack.md`                      |
| Find compiled summaries               | `kb/compiled/`                                 |

---

## Verticals (11)

### Core Verticals (4)

| Vertical | Files | Last Updated | TAM | Diagnostic Price | 12-Mo Portfolio |
|----------|-------|-------------|-----|-----------------|-----------------|
| [Mining](verticals/mining/README.md) | 9 | 2026-04-02 | R$248B+ revenue | R$25–75K | R$1.3–3M |
| [Investment Advisory](verticals/investment-advisory/README.md) | 9 | 2026-04-02 | R$7.9T AuC | R$25–80K | R$650K–1.25M |
| [Insurance/Surety](verticals/insurance-surety/README.md) | 9 | 2026-04-02 | R$751B+ premiums | R$25–75K | R$1.5–3M |
| [Auctions](verticals/auctions/README.md) | 9 | 2026-04-02 | R$200B+ moved | R$35–75K | R$800K–1.35M |

### Expansion Verticals (7)

| Vertical | Files | Last Updated | TAM | Active Projects |
|----------|-------|-------------|-----|----------------|
| [Real Estate](verticals/real-estate/README.md) | 9 | 2026-04-02 | R$500B+ PIB Construção | florida-flip, leila-do-leilao, incorporacoes-gestao |
| [GovTech](verticals/govtech/README.md) | 9 | 2026-04-02 | R$800B+ procurement | licitaleads, ceap-deputy-expenses, licenciaminer |
| [Energy & Infrastructure](verticals/energy-infrastructure/README.md) | 9 | 2026-04-02 | R$100B+ GD invested | kiiry-dashboard, kiiry-crm |
| [Automotive](verticals/automotive/README.md) | 9 | 2026-04-02 | R$500B+ used cars | deixacomigo |
| [Education & HR](verticals/education-hr/README.md) | 9 | 2026-04-02 | R$14B+ HR+EdTech | cv10x |
| [Financial Services](verticals/financial-services/README.md) | 9 | 2026-04-02 | R$600B+ fintech credit | florida-flip, licitaleads (cross-vertical) |
| [Construction](verticals/construction/README.md) | 9 | 2026-04-02 | R$500B+ PIB Construção | incorporacoes-gestao (cross-vertical) |

---

## Cross-Vertical Patterns (6)

| Pattern | Applies To | File |
|---------|-----------|------|
| Compliance Automation | All verticals | [patterns/compliance-automation.md](patterns/compliance-automation.md) |
| Data Integration | All verticals | [patterns/data-integration.md](patterns/data-integration.md) |
| Document Intelligence | Mining, Insurance, Auctions, Real Estate, GovTech, Financial | [patterns/document-intelligence.md](patterns/document-intelligence.md) |
| Predictive Models | All verticals | [patterns/predictive-models.md](patterns/predictive-models.md) |
| Alert/Notification | All verticals | [patterns/alert-notification.md](patterns/alert-notification.md) |
| Client 360 | Investment, Insurance, Mining, Financial, Energy | [patterns/client-360.md](patterns/client-360.md) |

---

## Projects (10)

| Project | Slug | Vertical Relevance | Type |
|---------|------|-------------------|------|
| [FloridaFlip](projects/florida-flip/README.md) | florida-flip | Real Estate Intelligence | Dashboard / Market Intelligence |
| [LicitaLeads](projects/licitaleads/README.md) | licitaleads | Insurance/Surety, Government | SaaS / Sales Intelligence |
| [Kiiry Dashboard](projects/kiiry-dashboard/README.md) | kiiry-dashboard | Investment Advisory | Internal / Financial Reporting |
| [LicenciaMiner](projects/licenciaminer/README.md) | licenciaminer | Mining | Dashboard / Regulatory Intelligence |
| [Leila do Leilão](projects/leila-do-leilao/README.md) | leila-do-leilao | Auctions | Dashboard / Real Estate Intelligence |
| [CEAP Dashboard](projects/ceap-deputy-expenses/README.md) | ceap-deputy-expenses | Government Transparency | Dashboard / Public Transparency |
| [DeixaComigo](projects/deixacomigo/README.md) | deixacomigo | Automotive | Lead Gen / Vertical SaaS |
| [CV10x](projects/cv10x/README.md) | cv10x | B2C Digital Product | SaaS / Info Product |
| [Kiiry CRM](projects/kiiry-crm/README.md) | kiiry-crm | B2B Sales | SaaS / B2B CRM |
| [Incorporações Gestão](projects/incorporacoes-gestao/README.md) | incorporacoes-gestao | Real Estate | SaaS / Financial Management |

---

## Agency Operations

| Topic | File |
|-------|------|
| Positioning & YC Strategy | [agency/positioning.md](agency/positioning.md) |
| Pricing Framework | [agency/pricing-framework.md](agency/pricing-framework.md) |
| Delivery Process | [agency/delivery-process.md](agency/delivery-process.md) |
| Quality Framework | [agency/quality-framework.md](agency/quality-framework.md) |
| Tech Stack | [agency/tech-stack.md](agency/tech-stack.md) |

---

## KB Commands

| Command | Purpose |
|---------|---------|
| `/project:add-research` | Ingest new research into raw/ |
| `/project:compile-vertical` | Recompile vertical from raw sources |
| `/project:lint-kb` | Check consistency and freshness |
| `/project:generate-report` | Generate compiled summaries |
| `/project:add-engagement` | Capture engagement learnings |
| `/project:update-index` | Regenerate all INDEX.md files |
| `/project:compile-portfolio` | Generate public HTML pages |

---

## KB Statistics

- **Total vertical files:** 99 (11 verticals × 9 files)
- **Cross-vertical patterns:** 6
- **Project directories:** 10
- **Agency docs:** 5
- **Raw sources:** 2 + research/
- **Compilation status:** All current (2026-04-02)
- **Next scheduled review:** 2026-07-02
