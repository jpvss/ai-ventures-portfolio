---
title: "Leila do Leilao — Learnings"
type: project
slug: leila-do-leilao
language: en
last_compiled: 2026-04-02
---

# Leila do Leilao — Learnings

## What Worked Well

- **True discount calculation via ITBI transaction data** — Cross-referencing Caixa auction catalog prices against BH municipal ITBI transaction records (2008-2026) revealed that advertised discounts are often misleading relative to actual market prices, producing a unique insight that no competing tool offers.
- **Multidimensional Deal Score with user-profile personalization** — Scoring properties across discount, occupancy status, modality, financing eligibility, and data confidence — then allowing users to reweight axes based on budget, objective, and risk tolerance via client-side localStorage — delivered tailored rankings without any backend infrastructure.
- **Modular Python pipeline with standalone modules** — Structuring the data pipeline as independent modules (ingestion, enrichment, geocoding, scoring) that each export static JSON for the frontend enabled incremental development, isolated debugging, and easy re-runs of individual stages.
- **Financial simulator with binary search bid optimization** — The maximum bid calculator uses binary search to find the highest bid price that still meets the investor's target ROI, accounting for municipality-specific ITBI, notary costs, SAC financing, and auctioneer commission — a level of specificity that generic calculators lack.
- **Leaflet map with Deal Score markers** — Interactive map with color-coded markers by Deal Score, floating detail panels, and sidebar listing provided geographic context that table-only views cannot convey, especially for identifying neighborhood-level opportunities.

## Challenges Encountered

- **Caixa catalog scraping fragility** — Caixa's property listing pages change structure frequently, use dynamic JavaScript rendering, and implement rate limiting, requiring httpx + BeautifulSoup4 scrapers with session management and periodic selector updates.
- **ITBI data coverage gaps** — BH municipal ITBI transaction data covers only Belo Horizonte metropolitan area; extending to other MG municipalities requires per-municipality data access requests with different formats and availability, limiting initial geographic scope.
- **Geocoding accuracy for auction properties** — Many Caixa properties list only partial addresses or neighborhood-level descriptions; geopy geocoding produces approximate coordinates that can place markers in wrong neighborhoods, requiring confidence scoring and manual review flags.
- **Occupied property risk assessment** — Properties flagged as occupied represent a significant legal and financial risk (eviction process), but Caixa's catalog data provides inconsistent or missing occupancy information, requiring heuristic classification from listing descriptions.

## Key Technical Decisions

- **Next.js 15 + static JSON over API-driven architecture** — Pre-computed all property scores and enrichments in the Python pipeline and exported as static JSON consumed by the Next.js frontend, eliminating runtime API dependencies and enabling fully static deployment — the right trade-off for a dataset that updates weekly, not in real-time.
- **Leaflet/React-Leaflet over Google Maps** — Chose Leaflet for map rendering to avoid Google Maps API costs on a project with potentially thousands of property markers, leveraging open-source tile layers and custom marker clustering.
- **Client-side scoring personalization via localStorage** — Implemented user profile preferences (budget, risk tolerance, investment objective) entirely client-side rather than building user accounts, reducing architecture complexity while still delivering personalized Deal Scores.
- **DuckDB for pipeline analytics** — Used DuckDB in the Python pipeline for analytical queries on ITBI transaction history (aggregations by neighborhood, year, property type) before exporting results as static JSON, leveraging its speed for exploratory analysis during development.

## Business Impact

- **Validated the auctions vertical with a concrete product** — Leila do Leilao demonstrated that auction intelligence is a viable consulting niche where ITBI transaction data creates a defensible data advantage — advisory firms can charge R$ 25k-50k for a white-label version.
- **Proved cross-dataset insight generation** — The core value proposition (true discount vs. advertised discount) emerges only from combining two datasets that no single source provides, establishing "cross-referencing for insight" as a replicable pattern across verticals.
- **Identified municipal tax data as an underexploited asset** — ITBI transaction records are public but underutilized; this project demonstrated their value for property valuation, insurance pricing, and credit collateral assessment — applicable beyond auctions.
- **Built reusable property analysis components** — The financial simulator, Deal Score engine, and map visualization components are portable to any real estate intelligence project, including FloridaFlip's pattern and future condominial investment tools.
