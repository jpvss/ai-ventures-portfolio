---
title: "LicenciaMiner"
type: project
slug: licenciaminer
vertical: mining
language: en
last_compiled: 2026-04-02
---

# LicenciaMiner

**Type:** Dashboard de dados / Regulatory intelligence tool

**Description:** Environmental licensing intelligence for mining with data from 14 official sources.

## Problem It Solves

Environmental consultancies and mining companies spend weeks manually searching IBAMA, ANM, and SEMAD portals to assess licensing feasibility. LicenciaMiner automatically cross-references 14 public sources — licenses, infractions, royalties, concessions, spatial restrictions — and delivers dossiers per company with approval rates, risk, and similar cases.

## Key Features

- Automated collection pipeline from 14 sources: IBAMA SISLIC, ANM SIGMINE/SCM/CFEM/RAL, SEMAD-MG (scraping), COPAM, ANA Outorgas, Receita Federal (CNPJ), geospatial data (UCs, TIs, biomes, caves)
- Analytical dashboard with 7 tabs: overview, data exploration, CNPJ lookup, decision analysis, concessions, geospatial map, and opportunity prospecting
- Intelligence dossier per CNPJ: company profile, decision history, IBAMA infractions, CFEM royalties, comparative approval rate, and similar cases
- Interactive map with ANM concession polygons, UC/TI layers, and spatial overlap detection
- Professional PDF report generation with risk analysis, 8 sections, and full source traceability

## Tech Stack

| Technology | Role |
|---|---|
| Python 3.11 | Backend language |
| Streamlit | Dashboard framework |
| DuckDB | Analytical query engine |
| Apache Parquet | Columnar data storage |
| Pandas | Data manipulation |
| Plotly | Interactive charts |
| Folium | Map rendering |
| GeoPandas | Geospatial data processing |
| Shapely | Geometric operations |
| httpx | Async HTTP client |
| Click | CLI for pipeline scripts |
| fpdf2 | PDF generation |
| PyMuPDF | PDF parsing |
| Anthropic SDK | LLM integration |
| Tenacity | Retry logic |

## Capabilities Demonstrated

- Ingestion and normalization of 14 simultaneous heterogeneous public sources (REST APIs, ArcGIS, Excel, HTML scraping, shapefiles, PDFs) with retry, rate limiting, and incremental collection
- Geospatial analysis with spatial joins between mining concession polygons and environmental restriction areas (UCs, TIs, biomes, caves) using GeoPandas/Shapely
- Domain-specific regulatory risk modeling with cross-referencing of environmental, mining, and cadastral data by CNPJ — including approval rate, infraction recurrence, and decision patterns by regional office/activity
- DuckDB/Parquet analytical architecture with materialized views over 12 datasets, cross-source queries by CNPJ, and Streamlit caching for performance in 1GB container
- Extraction and processing of regulatory documents: COPAM opinion scraping, SEMAD decision PDF download and OCR, cadastral enrichment via Receita Federal

## Target Opportunities

| Segment | Project Type | Price Range | MVP Timeline |
|---|---|---|---|
| Mining / Environmental consultancies | Environmental due diligence platform for mining projects | R$ 40k-70k | 3-4 weeks |
| ESG / Asset managers | Environmental compliance monitoring for investment portfolios | R$ 45k-80k | 3-4 weeks |
| Government / State environmental agencies | Management and analytics dashboard for licensing agencies | R$ 50k-90k | 4-5 weeks |
| Legal / Environmental law firms | Precedent research and analysis tool for environmental litigation | R$ 35k-60k | 3-4 weeks |

## Vertical Relevance

**Primary:** mining (environmental licensing, ANM concessions, CFEM royalties, mining regulatory compliance)

Also relevant to: investment-advisory (ESG monitoring, environmental due diligence for asset portfolios)

## Links

- **Deploy:** Not deployed (local/container)
- **Repository:** https://github.com/jpvss/licenciaminer
