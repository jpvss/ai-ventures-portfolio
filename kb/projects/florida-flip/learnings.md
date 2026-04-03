---
title: "FloridaFlip — Learnings"
type: project
slug: florida-flip
language: en
last_compiled: 2026-04-02
---

# FloridaFlip — Learnings

## What Worked Well

- **DuckDB + Parquet for in-browser analytics** — Running analytical queries over 2.1M property records directly in the browser eliminated the need for a traditional database server, cutting infrastructure costs to near-zero while maintaining sub-second query response times on filtered datasets.
- **Multidimensional ZIP-code scoring (9 dimensions)** — Combining vacancy, tenant quality, yield, risk, and 5 other axes into a single configurable score gave investors an opinionated-but-adjustable ranking that replaced hours of manual cross-referencing across data sources.
- **Reproducible Python ingestion pipeline** — Building a standalone Python pipeline that normalizes data from FDOR, FEMA, Census ACS, and Redfin into a single Parquet file made the entire dataset rebuildable from scratch, ensuring data freshness and auditability.
- **Domain-specific financial calculators** — Implementing flip/hold/BRRRR calculators with Florida-specific closing costs, OIR insurance rules, and NFIP flood insurance premiums differentiated the tool from generic real estate calculators and demonstrated deep domain modeling capability.
- **Choropleth map with drill-down** — Google Maps API with county-level choropleth by selectable metric (price, inventory, days on market) across all 67 Florida counties provided immediate geographic context that static dashboards cannot match.

## Challenges Encountered

- **Data heterogeneity across 67 counties** — FDOR assessment data varies significantly in format and completeness across Florida counties; normalization required per-county parsing rules and extensive null handling to achieve uniform schema coverage.
- **DuckDB browser bundle size** — The DuckDB WASM module adds significant payload to the initial page load; balancing between server-side and client-side query execution required careful architecture to avoid degraded first-load experience.
- **Stale public data sources** — FEMA flood maps and Census ACS data update on different cadences (some annually, some every 5 years), creating temporal mismatches that required explicit freshness metadata and user-facing data vintage indicators.
- **Parquet file size management** — 2.1M properties with multiple attributes per record produce multi-hundred-MB Parquet files; partitioning by county and implementing lazy loading was necessary to keep Vercel deployment within limits.

## Key Technical Decisions

- **Next.js 16 + DuckDB instead of traditional backend + PostgreSQL** — Chose a serverless-first architecture with analytical queries running on Parquet files rather than a managed database, trading real-time write capability (unnecessary for batch-updated public data) for zero operational cost and simpler deployment on Vercel.
- **Python pipeline separate from Next.js app** — Kept data ingestion as a standalone Python project rather than building it into the Next.js app, enabling independent scheduling of data refreshes and leveraging Python's superior ecosystem for geospatial processing (GeoPandas, shapefile parsing).
- **Configurable scoring weights** — Made the 9-dimension submarket scoring fully configurable by the user rather than hardcoding weights, acknowledging that different investor profiles (cash buyer vs. leveraged, flip vs. hold) have fundamentally different risk/return preferences.
- **Static JSON export for frontend** — Pre-computed scoring and aggregations during the pipeline phase and exported as static JSON, avoiding runtime computation costs and enabling CDN caching of computed metrics.

## Business Impact

- **Proved the "territorial intelligence panel" pattern** — Demonstrated that aggregating heterogeneous public data sources into a scored, map-driven dashboard is a repeatable consulting deliverable applicable to real estate, agribusiness, retail expansion, and credit risk — with R$ 30k-90k engagement pricing.
- **Validated DuckDB/Parquet as a consulting-friendly stack** — Showed that million-record analytical dashboards can be built and deployed without database infrastructure, dramatically reducing client hosting costs and ongoing maintenance burden — a key differentiator for mid-market consulting engagements.
- **Generated reusable geospatial visualization components** — The choropleth map, property search, and drill-down UI components built for FloridaFlip are directly portable to any geographic intelligence project (land evaluation, store expansion, mortgage risk).
- **Established Florida real estate domain expertise** — Deep modeling of FL-specific rules (OIR closing costs, NFIP insurance, 67-county FDOR data) creates a defensible knowledge moat for future engagements in real estate investment advisory.
