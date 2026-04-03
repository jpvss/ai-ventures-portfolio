---
title: "Kiiry Dashboard — Architecture"
type: project
slug: kiiry-dashboard
language: en
last_compiled: 2026-04-02
---

# Kiiry Dashboard — Technical Architecture

## Tech Stack Choices and Rationale

- **Python 3.13 + Flask:** Lightweight backend for data processing and rendering. Python ecosystem (Pandas, WeasyPrint) is ideal for financial ETL and document generation.
- **Pandas:** Core data manipulation for multi-source Excel ingestion, tariff calculations, and reconciliation across CEMIG and Cogni data.
- **Pydantic v2:** Strict validation of financial data at ingestion boundaries — critical for auditable calculations where cent-level precision matters.
- **WeasyPrint:** HTML-to-PDF generation for investor-grade financial reports with full formatting control.
- **structlog:** Structured logging for debugging complex financial calculations across multiple plants and periods.
- **Railway:** PaaS deployment with git push — zero DevOps overhead for internal tool.
- **TOML configuration:** Plant and tariff configurations managed as code rather than database records.

## Data Architecture

- **Input sources:** CEMIG Excel reports (multi-tab, per-UC compensation data), Cogni platform exports (invoices, boletos, UC mapping)
- **Processing:** Pandas pipeline with aliasing, normalization, cross-validation between sources
- **Storage:** In-memory cache — no database. Data re-processed from Excel uploads each session.
- **Output:** Rendered HTML dashboards + WeasyPrint PDF reports with audit JSON per plant/month

## Key Technical Patterns

- **Domain-specific financial modeling:** CEMIG tariff rules, GD I/II compensation, PIS/COFINS, ICMS, Fio B — all encoded as business rules in Python
- **Multi-source ETL with cross-validation:** CEMIG data vs. Cogni billing reconciliation with diff reporting
- **Auditable calculation pipeline:** Every computed value traces back to source data, formula, and rounding decision
- **Zero-database architecture:** All state derived from uploaded Excel files — serverless-friendly, no migration overhead
- **Multi-state payment tracking:** 5-state payment status model with sector-specific transition rules

<!-- TO BE ENRICHED: Add learnings from project development -->

## Performance Considerations

- In-memory Pandas processing — no database round-trips
- Per-plant/period caching to avoid redundant calculations
- WeasyPrint PDF generation is CPU-intensive — batched for multiple plants

<!-- TO BE ENRICHED: Add learnings from project development -->

## Deployment Architecture

- Railway PaaS with Gunicorn WSGI
- Git push deployment with auto-scaling
- No persistent database — stateless processing

<!-- TO BE ENRICHED: Add learnings from project development -->
