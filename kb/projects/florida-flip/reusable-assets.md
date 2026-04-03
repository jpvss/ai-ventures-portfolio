---
title: "FloridaFlip — Reusable Assets"
type: project
slug: florida-flip
language: en
last_compiled: 2026-04-02
---

# FloridaFlip — Reusable Assets

## Technical Components

- **DuckDB/Parquet analytical engine:** Pattern for running OLAP queries over millions of records with zero database infrastructure. Reusable for any data-intensive dashboard (see `kb/patterns/` for cross-vertical pattern).
- **Multidimensional scoring system:** 9-dimension scoring with configurable weights — applicable to any domain requiring ranked evaluation (leads, properties, risk).
- **Python data ingestion pipeline:** Reproducible ETL for heterogeneous public data sources with normalization — adaptable to Brazilian government data sources.
- **Choropleth map component:** County/region-level choropleth with drill-down, built on Google Maps API — reusable for any geo-intelligence dashboard.
- **PDF report generator:** Client-side jsPDF report generation with KPIs and charts — reusable for investor-facing or executive reports.
- **Financial calculator components:** Flip/hold/BRRRR calculators with domain-specific cost modeling — pattern transferable to other financial simulation tools.

## Patterns That Map to kb/patterns/

- Public data ingestion and normalization (cross-reference: `kb/patterns/public-data-ingestion.md`)
- Geospatial intelligence dashboard (cross-reference: `kb/patterns/geospatial-intelligence.md`)
- Multidimensional scoring and ranking (cross-reference: `kb/patterns/scoring-engine.md`)
- DuckDB/Parquet zero-infra analytics (cross-reference: `kb/patterns/duckdb-parquet-analytics.md`)

## Data Sources and Integrations

- **FDOR (Florida Department of Revenue):** Property assessor data — pattern for US public records ingestion
- **FEMA flood zones:** Risk data integration — reusable for insurance/risk products
- **Census ACS:** Demographic overlay for market intelligence — applicable across verticals
- **Redfin market data:** Real estate market metrics ingestion — pattern for scraping/API market data providers
- **Google Maps API integration:** Geocoding, place search, and map rendering — reusable across all geo-enabled projects
