---
title: "Kiiry Dashboard — Reusable Assets"
type: project
slug: kiiry-dashboard
language: en
last_compiled: 2026-04-02
---

# Kiiry Dashboard — Reusable Assets

## Technical Components

- **Multi-source Excel ETL pipeline:** Pandas-based ingestion of multi-tab Excel files with aliasing, normalization, and cross-validation. Reusable for any financial reconciliation tool.
- **Auditable financial calculation engine:** Every computed value traced to source, formula, and rounding decision. Pattern for compliance-ready financial tools.
- **WeasyPrint PDF report generator:** HTML-to-PDF generation for investor-grade financial reports with Jinja2 templates. Reusable for any domain requiring formatted PDF output.
- **Multi-state payment tracker:** 5-state payment status model (PAGO, Inadimplente, Em Aberto, Nao Emitido, Inadimplente Anterior) with business rule transitions. Adaptable for billing systems.
- **Domain-specific tariff calculator:** CEMIG tariff rules, GD I/II compensation encoding. Pattern for regulatory financial modeling.
- **Audit trail system:** Per-entity/period audit JSON with diff between expected and actual values. Reusable for any reconciliation or compliance tool.

## Patterns That Map to kb/patterns/

- Financial ETL and reconciliation (cross-reference: `kb/patterns/financial-etl.md`)
- Auditable document generation (cross-reference: `kb/patterns/auditable-reporting.md`)
- Domain-specific regulatory modeling (cross-reference: `kb/patterns/regulatory-modeling.md`)
- Zero-database architecture (cross-reference: `kb/patterns/zero-infra-data-product.md`)

## Data Sources and Integrations

- **CEMIG reports:** Multi-tab Excel with per-UC compensation data — pattern for utility company data ingestion
- **Cogni platform:** Billing/invoicing data export — pattern for SaaS platform data integration
- **ANEEL/SIGA:** Solar plant registry data — available as public data for energy sector products
- **CCEE:** Generation and compensation data for registered plants
