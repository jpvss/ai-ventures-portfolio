---
title: "FloridaFlip — Architecture"
type: project
slug: florida-flip
language: en
last_compiled: 2026-04-02
---

# FloridaFlip — Technical Architecture

## Tech Stack Choices and Rationale

- **DuckDB + Apache Parquet:** Enables analytical queries over 2.1M property records directly in-browser and server-side without an external database. Eliminates infrastructure cost and latency for OLAP-style queries on structured columnar data.
- **Next.js 16 + React 19:** Full-stack framework with Server Components for data-heavy pages and client interactivity where needed.
- **Google Maps API:** Industry-standard geospatial visualization for choropleth maps over 67 Florida counties with polygon rendering.
- **Python data pipeline:** Reproducible ETL for ingesting and normalizing heterogeneous public sources (FDOR, FEMA, Census ACS, Redfin) into Parquet files.
- **jsPDF:** Client-side PDF generation for executive reports without server-side dependencies.
- **Vercel:** Zero-config deployment with edge functions for DuckDB queries.

## Data Architecture

- **Source data:** Public datasets from FDOR (property assessor), FEMA (flood zones), Census ACS (demographics), Redfin (market metrics)
- **Storage:** Parquet files (columnar, compressed) served as static assets or loaded via DuckDB
- **Query layer:** DuckDB running both server-side (API routes) and client-side (WASM) for analytical queries
- **No external database:** All data is pre-processed and stored as Parquet — zero database infrastructure

## Key Technical Patterns

- **Multidimensional scoring:** 9-dimension scoring system with configurable weights for submarket ranking by ZIP code
- **Domain-specific financial modeling:** Flip/hold/BRRRR calculators incorporating Florida-specific regulatory costs (OIR, NFIP)
- **Choropleth visualization:** County-level map rendering with metric-driven color scales and drill-down
- **Static data + dynamic queries:** Pre-processed Parquet files queried dynamically via DuckDB — combines static site benefits with analytical flexibility

<!-- TO BE ENRICHED: Add learnings from project development -->

## Performance Considerations

- DuckDB/Parquet enables sub-second queries over millions of records without database provisioning
- Parquet columnar format minimizes data transfer — only requested columns are read
- Client-side DuckDB WASM reduces server load for interactive exploration

<!-- TO BE ENRICHED: Add learnings from project development -->

## Deployment Architecture

- Vercel hosting with static Parquet assets
- Python pipeline runs locally/CI to regenerate data files
- No persistent server — fully serverless

<!-- TO BE ENRICHED: Add learnings from project development -->
