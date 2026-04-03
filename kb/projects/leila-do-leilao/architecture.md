---
title: "Leila do Leilao — Architecture"
type: project
slug: leila-do-leilao
language: en
last_compiled: 2026-04-02
---

# Leila do Leilao — Technical Architecture

## Tech Stack Choices and Rationale

- **Next.js 15 + React 19:** Full-stack framework for data-heavy pages with Server Components and client-side interactivity for map and financial simulators.
- **Leaflet / React-Leaflet:** Open-source map library for property visualization with custom markers, clustering, and interactive popups. Lighter alternative to Google Maps for dense marker rendering.
- **DuckDB:** Analytical queries over ITBI transaction history for neighborhood trend analysis and comparable property lookups.
- **Python pipeline (Pandas + httpx + BeautifulSoup4):** Modular data pipeline for scraping Caixa catalogs, parsing ITBI data, geocoding addresses, and computing Deal Scores.
- **Pydantic v2:** Strict validation of scraped and parsed property data — critical when dealing with inconsistent public data sources.
- **geopy:** Geocoding addresses to coordinates for map placement and distance calculations.
- **Google Maps API:** Street View imagery, Places API for nearby amenities, and Directions API for commute times on property detail pages.

## Data Architecture

- **Sources:** Caixa CSV catalogs (daily property listings), BH municipal ITBI records (2008-2026 transactions), scraped detail pages (property specifics, liens, risks)
- **Pipeline:** Python modules (ingestion -> enrichment -> geocoding -> scoring) each producing JSON artifacts
- **Frontend data:** Static JSON files consumed by Next.js — no runtime database
- **Query layer:** DuckDB for ITBI trend analysis and comparable lookups

## Key Technical Patterns

- **Cross-dataset insight generation:** Combining Caixa appraisal with real ITBI transaction data to reveal true market discount — pattern for any "advertised vs. actual" analysis
- **Multidimensional Deal Score:** 5-factor scoring (discount, occupancy, modality, financing, data confidence) with user-configurable weights
- **Client-side personalization:** User profile stored in localStorage with dynamic score reweighting — no backend required for personalization
- **Modular pipeline architecture:** Each Python module runs standalone and exports JSON — enables incremental processing and debugging
- **Financial simulation engine:** ROI, SAC financing, maximum bid via binary search — all client-side computation

<!-- TO BE ENRICHED: Add learnings from project development -->

## Performance Considerations

- Static JSON for fast page loads without database queries
- Leaflet for efficient rendering of hundreds of map markers
- Client-side DuckDB for ITBI trend queries without server round-trips

<!-- TO BE ENRICHED: Add learnings from project development -->

## Deployment Architecture

- Next.js static export or Vercel deployment
- Python pipeline runs locally to regenerate JSON data
- No persistent server or database

<!-- TO BE ENRICHED: Add learnings from project development -->
