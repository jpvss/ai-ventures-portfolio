---
title: "Projects Index"
type: index
language: en
last_compiled: 2026-04-02
---

# Projects Index

Master index of all 10 portfolio projects with vertical mapping and key capabilities.

## Project Overview

| # | Slug | Name | Vertical | Status | Key Capabilities |
|---|---|---|---|---|---|
| 1 | [florida-flip](florida-flip/README.md) | FloridaFlip | investment-advisory | Deployed | DuckDB/Parquet analytics, geospatial choropleth, multidimensional scoring, financial modeling |
| 2 | [licitaleads](licitaleads/README.md) | LicitaLeads | insurance-surety | Deployed | Government data ingestion, CNPJ enrichment, lead scoring, zero-infra data product |
| 3 | [kiiry-dashboard](kiiry-dashboard/README.md) | Kiiry Dashboard | investment-advisory | Deployed | Financial ETL, auditable reporting, regulatory modeling, PDF generation |
| 4 | [licenciaminer](licenciaminer/README.md) | LicenciaMiner | mining | Local/Container | 14-source data fusion, geospatial overlap detection, regulatory risk scoring, CNPJ dossier |
| 5 | [leila-do-leilao](leila-do-leilao/README.md) | Leila do Leilao | auctions | Not deployed | Cross-dataset insight (ITBI), Deal Score, financial simulation, map visualization |
| 6 | [ceap-deputy-expenses](ceap-deputy-expenses/README.md) | CEAP Dashboard | adjacent | Deployed | Fraud detection (Benford, HHI), D3.js visualizations, fuzzy matching, Cloudflare edge |
| 7 | [deixacomigo](deixacomigo/README.md) | DeixaComigo | adjacent | Deployed | FIPE pricing engine, lead capture funnel, programmatic SEO, Supabase RLS |
| 8 | [cv10x](cv10x/README.md) | CV10x | adjacent | Deployed | LLM structured output, B2C funnel, marketing automation, server-side tracking |
| 9 | [kiiry-crm](kiiry-crm/README.md) | Kiiry CRM | adjacent | Deployed | Google Places lead import, CRM Kanban, multi-territory team mgmt, tariff classification |
| 10 | [incorporacoes-gestao](incorporacoes-gestao/README.md) | Incorporacoes Gestao | investment-advisory | Deployed | Precision apportionment, 3-layer access control, DWG/DXF processing, 3D viewer |

## Vertical Distribution

| Vertical | Projects | Count |
|---|---|---|
| mining | licenciaminer | 1 |
| investment-advisory | florida-flip, kiiry-dashboard, incorporacoes-gestao | 3 |
| insurance-surety | licitaleads | 1 |
| auctions | leila-do-leilao | 1 |
| adjacent | ceap-deputy-expenses, deixacomigo, cv10x, kiiry-crm | 4 |

## Cross-Cutting Capabilities

The following capabilities appear across multiple projects:

| Capability | Projects |
|---|---|
| Public data ingestion & normalization | florida-flip, licitaleads, licenciaminer, ceap-deputy-expenses, leila-do-leilao |
| Multidimensional scoring engine | florida-flip, licitaleads, leila-do-leilao, kiiry-crm, deixacomigo |
| DuckDB/Parquet analytics | florida-flip, licenciaminer, ceap-deputy-expenses, leila-do-leilao |
| CNPJ enrichment pipeline | licitaleads, licenciaminer, ceap-deputy-expenses |
| Geospatial visualization | florida-flip, licenciaminer, leila-do-leilao |
| Domain-specific financial modeling | florida-flip, kiiry-dashboard, leila-do-leilao, incorporacoes-gestao |
| PDF report generation | florida-flip, kiiry-dashboard, licenciaminer, incorporacoes-gestao |
| Auditable calculation/reporting | kiiry-dashboard, incorporacoes-gestao |
| Lead generation funnel | deixacomigo, cv10x, licitaleads |
| LLM integration | cv10x, licenciaminer |
| Regulatory compliance modeling | licitaleads, kiiry-dashboard, licenciaminer, kiiry-crm, incorporacoes-gestao |

## Per-Project Files

Each project directory contains 4 files:

- `README.md` — Project summary, features, tech stack, vertical mapping, opportunities
- `architecture.md` — Technical architecture, stack rationale, data architecture, patterns
- `learnings.md` — What worked, challenges, decisions, impact (skeleton — TO BE ENRICHED)
- `reusable-assets.md` — Extractable components, pattern cross-references, data sources
