---
title: "LicenciaMiner — Learnings"
type: project
slug: licenciaminer
language: en
last_compiled: 2026-04-02
---

# LicenciaMiner — Learnings

## What Worked Well

- **14-source ingestion pipeline with retry and rate limiting** — Building a unified collection pipeline across REST APIs (ANM SIGMINE/SCM/CFEM/RAL), ArcGIS services, Excel downloads, HTML scraping (SEMAD-MG), shapefiles, and PDFs (COPAM opinions) proved that heterogeneous government data can be systematically normalized when each source adapter handles its own retry logic via Tenacity.
- **DuckDB/Parquet analytical architecture in 1GB container** — Running materialized views over 12 datasets with cross-source CNPJ joins inside a Streamlit app constrained to 1GB RAM demonstrated that DuckDB's memory-efficient columnar engine is viable for complex regulatory analytics without dedicated database infrastructure.
- **Geospatial overlap detection with GeoPandas/Shapely** — Spatial joins between ANM concession polygons and environmental restriction layers (UCs, TIs, biomes, caves) provided automated risk signals that consultancies previously assessed manually using QGIS — reducing feasibility assessment time from days to minutes.
- **CNPJ-based intelligence dossiers** — Cross-referencing a single CNPJ across IBAMA infractions, CFEM royalties, SEMAD decisions, ANM concessions, and Receita Federal cadastral data produced comprehensive company profiles that no single government portal offers.
- **Folium maps with multi-layer visualization** — Rendering ANM concession polygons alongside UC/TI restriction layers on interactive Folium maps with overlap highlighting gave users immediate spatial context for licensing feasibility.

## Challenges Encountered

- **SEMAD-MG portal instability and anti-scraping measures** — Minas Gerais' state environmental agency portal frequently changes HTML structure, implements CAPTCHAs, and has unpredictable downtime, requiring robust scraping with session management, retry backoff, and fallback to cached data.
- **PDF extraction from regulatory decisions** — COPAM opinions and SEMAD decisions arrive as scanned or semi-structured PDFs with inconsistent layouts; PyMuPDF extraction required document-type-specific parsing rules and OCR fallback for older scanned documents.
- **Shapefile coordinate system inconsistencies** — Different government sources use different coordinate reference systems (SIRGAS 2000, WGS 84, SAD 69), requiring systematic reprojection before spatial joins — errors in CRS handling produce silent false negatives in overlap detection.
- **CNPJ matching across sources with inconsistent formatting** — Government databases store CNPJs with and without punctuation, with leading zeros sometimes stripped, and with subsidiary vs. headquarters CNPJ confusion, requiring normalization and fuzzy matching logic.

## Key Technical Decisions

- **Streamlit over Next.js for the dashboard** — Chose Streamlit for rapid prototyping of a data-heavy analytical tool with 7 tabs, leveraging Python's superior geospatial ecosystem (GeoPandas, Shapely, Folium) directly in the UI layer without API serialization overhead — the right choice for an internal/consultant-facing tool where developer velocity outweighs UI polish.
- **DuckDB with Parquet over PostgreSQL** — Used DuckDB's analytical engine over Parquet files instead of a traditional RDBMS, enabling complex cross-source queries with materialized views while keeping the deployment footprint to a single container with no external database dependency.
- **Anthropic SDK for LLM-assisted analysis** — Integrated Claude for natural language interpretation of regulatory decisions and risk narrative generation in PDF reports, adding a qualitative layer that pure data analysis cannot provide.
- **Click CLI for pipeline orchestration** — Built each data source adapter as a Click CLI command, enabling selective re-ingestion of individual sources without running the full pipeline — critical for debugging and for handling sources that update on different schedules.

## Business Impact

- **Validated the mining vertical as a consulting opportunity** — LicenciaMiner demonstrated that environmental licensing intelligence is a high-value, underserved niche: consultancies currently spend R$ 5k-15k per manual feasibility study, and a platform approach could serve multiple clients at R$ 40k-90k per engagement.
- **Proved multi-source regulatory intelligence is a repeatable pattern** — The architecture of "collect from N government sources, normalize by entity key, cross-reference for risk signals, deliver as dossier" is directly applicable to insurance-surety (SUSEP + ANS + Receita Federal), auctions (tribunals + cartórios + registries), and investment advisory (CVM + B3 + Receita Federal).
- **Established geospatial analysis as a differentiator** — Spatial overlap detection between concessions and environmental restrictions is a capability that generic BI tools cannot replicate, creating a technical moat for mining and real estate vertical engagements.
- **Built domain expertise in Brazilian environmental regulation** — Deep familiarity with IBAMA SISLIC, ANM SIGMINE, SEMAD-MG, COPAM, and ANA Outorgas processes positions the agency for environmental due diligence engagements in mining, infrastructure, and ESG compliance.
