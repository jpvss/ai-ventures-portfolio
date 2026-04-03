---
title: "LicenciaMiner — Architecture"
type: project
slug: licenciaminer
language: en
last_compiled: 2026-04-02
---

# LicenciaMiner — Technical Architecture

## Tech Stack Choices and Rationale

- **Python 3.11 + Streamlit:** Rapid prototyping for data-intensive analytical dashboards. Streamlit provides built-in caching, session state, and reactive widgets without frontend build tooling.
- **DuckDB + Parquet:** Analytical queries over 12 datasets with materialized views — enables cross-source CNPJ lookups and aggregations without external database infrastructure. Fits in 1GB container memory.
- **GeoPandas + Shapely:** Geospatial analysis for spatial joins between mining concession polygons and environmental restriction areas (UCs, TIs, biomes, caves). Industry-standard Python geospatial stack.
- **Folium:** Leaflet-based map rendering with polygon overlays for concession visualization. Lightweight and Streamlit-compatible.
- **httpx:** Async HTTP client for parallel data collection from 14 sources with connection pooling and timeout management.
- **Tenacity:** Retry logic with exponential backoff for unreliable government API endpoints.
- **Anthropic SDK:** LLM integration for natural language analysis of regulatory decisions and report generation.
- **Click:** CLI framework for pipeline scripts — separation of data collection from dashboard rendering.

## Data Architecture

- **14 source types:** REST APIs (ANM SIGMINE, BrasilAPI), ArcGIS Feature Services (ANM concessions, UCs, TIs), Excel downloads (CFEM, RAL), HTML scraping (SEMAD-MG, COPAM), Shapefiles (biomes, caves), PDFs (SEMAD decisions)
- **Storage:** Parquet files organized by source with standardized schemas
- **Query layer:** DuckDB with materialized views for cross-source queries by CNPJ
- **Caching:** Streamlit session-state caching for dashboard performance

## Key Technical Patterns

- **Multi-source data fusion:** 14 heterogeneous sources normalized into a unified queryable layer via DuckDB views
- **Geospatial overlap detection:** Spatial joins between concession polygons and restriction zones to flag regulatory risk
- **CNPJ-centric intelligence:** All data cross-referenced by company identifier for comprehensive dossier generation
- **Incremental collection:** Pipeline supports resume-safe incremental collection with checkpoint tracking
- **Regulatory risk scoring:** Approval rate calculation, infraction recurrence analysis, and decision pattern detection by regional office

<!-- TO BE ENRICHED: Add learnings from project development -->

## Performance Considerations

- DuckDB materialized views pre-compute cross-source joins for interactive dashboard performance
- Streamlit caching reduces redundant data loading within session
- Parquet columnar format minimizes I/O for selective column reads
- 1GB container constraint drives aggressive data pruning and view materialization

<!-- TO BE ENRICHED: Add learnings from project development -->

## Deployment Architecture

- Containerized deployment (Docker) with all data pre-loaded as Parquet files
- CLI pipeline runs separately to refresh data
- No external database dependencies

<!-- TO BE ENRICHED: Add learnings from project development -->
