---
title: "Kiiry Dashboard"
type: project
slug: kiiry-dashboard
vertical: investment-advisory
language: en
last_compiled: 2026-04-02
---

# Kiiry Dashboard

**Type:** Ferramenta interna / Financial reporting platform

**Description:** Financial management and reporting platform for solar power plant investors.

## Problem It Solves

Owners of distributed solar plants in Brazil need to provide monthly accountability reports to investors on compensated energy, revenues, and payments. Today this process is manual, cross-referencing CEMIG data with billing platform (Cogni) spreadsheets, prone to errors that affect real payments to lessors and investors.

## Key Features

- Monthly report per plant with revenue balance by UC (consumer unit), including compensated energy, tariffs, lessor revenue, and payment status
- Automated financial calculation pipeline: Excel ingestion (CEMIG + Cogni), dynamic compensable tariff calculation (GD I/II), delinquency classification, and total generation
- Multi-plant management dashboard with KPIs (total revenue, delinquency %, injected energy) and MBR matrix of all plants x periods
- PDF generation via WeasyPrint for investor reports and sales commissions with built-in audit trail
- Complete audit trail: tooltips with formulas, per-plant/month audit JSON, and audit panel with diff between Cogni and calculated values

## Tech Stack

| Technology | Role |
|---|---|
| Python 3.13 | Backend language |
| Flask | Web framework |
| Gunicorn | WSGI server |
| Pandas | Data manipulation and ETL |
| Pydantic v2 | Data validation |
| Jinja2 | Template rendering |
| WeasyPrint | PDF generation |
| Tailwind CSS | Styling |
| Babel | i18n / date formatting |
| structlog | Structured logging |
| TOML | Configuration |
| Railway | Deployment |

## Capabilities Demonstrated

- Domain-specific financial modeling with Brazilian electric sector regulatory rules (CEMIG tariffs, GD I/II compensation, PIS/COFINS, ICMS, Fio B)
- Robust ETL pipeline for heterogeneous multi-source data (multi-tab CEMIG Excel, Cogni Invoices/Boletos/UCs) with normalization, aliasing, and cross-validation
- Auditable financial document generation with complete traceability of every calculation (formulas, sources, rounding) — compliance-ready
- Serverless-friendly architecture with in-memory cache, zero database, and continuous deploy via git push (Railway)
- Multi-state payment status management (PAGO, Inadimplente, Em Aberto, Nao Emitido, Inadimplente Anterior) with solar energy sector-specific business rules

## Target Opportunities

| Segment | Project Type | Price Range | MVP Timeline |
|---|---|---|---|
| Solar Energy / GD integrators | White-label billing and management platform for GD plants | R$ 50k-90k | 4-5 weeks |
| Accounting / Agro & energy firms | Automated financial reconciliation for rural lessors | R$ 30k-50k | 3-4 weeks |
| Utilities / Energy commercializers | Delinquency and revenue monitoring dashboard | R$ 40k-70k | 3-4 weeks |
| Investment Funds / FIPs | Operational and financial performance panel for solar portfolios | R$ 60k-120k | 4-6 weeks |

## Vertical Relevance

**Primary:** investment-advisory (investor reporting, financial modeling for solar asset portfolios)

Also relevant to: adjacent (energy sector management, accounting automation)

## Links

- **Deploy:** https://web-production-175e67.up.railway.app
- **Repository:** https://github.com/jpvss/kiiry-dashboard
