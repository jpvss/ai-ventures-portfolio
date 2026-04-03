---
title: "LicenciaMiner — Reusable Assets"
type: project
slug: licenciaminer
language: en
last_compiled: 2026-04-02
---

# LicenciaMiner — Reusable Assets

## Technical Components

- **14-source data collection pipeline:** Multi-format ingestion (REST, ArcGIS, Excel, scraping, shapefiles, PDFs) with retry, rate limiting, and incremental checkpointing. Most comprehensive public data pipeline in the portfolio.
- **Geospatial overlap detector:** Spatial joins between polygons using GeoPandas/Shapely for restriction zone identification. Reusable for any land-use or territorial analysis.
- **CNPJ intelligence dossier generator:** Cross-source company profile aggregation with approval rates, infractions, royalties. Pattern for B2B intelligence products.
- **Regulatory risk scorer:** Approval rate calculation and infraction recurrence analysis by company, activity type, and regional office. Adaptable to other regulatory domains.
- **DuckDB materialized view architecture:** Cross-source analytical queries over 12 datasets within constrained memory. Pattern for resource-constrained analytical applications.
- **PDF report generator with risk analysis:** 8-section professional report with source traceability. Reusable for due diligence and compliance reporting.

## Patterns That Map to kb/patterns/

- Public data ingestion and normalization (cross-reference: `kb/patterns/public-data-ingestion.md`)
- Geospatial intelligence dashboard (cross-reference: `kb/patterns/geospatial-intelligence.md`)
- CNPJ enrichment pipeline (cross-reference: `kb/patterns/cnpj-enrichment.md`)
- DuckDB/Parquet zero-infra analytics (cross-reference: `kb/patterns/duckdb-parquet-analytics.md`)
- Compliance automation (cross-reference: `kb/patterns/compliance-automation.md`)
- Regulatory modeling (cross-reference: `kb/patterns/regulatory-modeling.md`)

## Data Sources and Integrations

- **IBAMA SISLIC:** Environmental licenses by activity, developer, and location
- **ANM SIGMINE:** Mining process registry with geometry (ArcGIS FeatureServer)
- **ANM SCM:** Mining concessions with holder and substance data
- **ANM CFEM:** Mining royalty payments by company and municipality
- **ANM RAL:** Annual mining reports
- **SEMAD-MG:** State environmental licensing decisions (scraped)
- **COPAM:** Environmental council meeting minutes and opinions
- **ANA:** Water use permits (outorgas)
- **Receita Federal:** CNPJ cadastral data for company enrichment
- **ICMBio/IBGE:** Conservation units, indigenous territories, biomes (shapefiles)
- **Cave registry:** Speleological data for impact assessment
