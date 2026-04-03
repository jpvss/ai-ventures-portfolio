---
title: "Leila do Leilao — Reusable Assets"
type: project
slug: leila-do-leilao
language: en
last_compiled: 2026-04-02
---

# Leila do Leilao — Reusable Assets

## Technical Components

- **ITBI transaction data pipeline:** Ingestion and normalization of municipal ITBI records for market price benchmarking. Reusable for any property valuation or tax intelligence product.
- **Multidimensional Deal Score engine:** 5-factor scoring with user-configurable weights and profile-based reweighting. Pattern for any investment decision tool.
- **Financial simulation suite:** ROI calculator, SAC financing model, maximum bid solver (binary search), ITBI/notary cost estimator. Reusable for any real estate financial product.
- **Caixa catalog scraper:** CSV ingestion + detail page scraping for Caixa property listings. Adaptable for Banco do Brasil, EMGEA, and private auctioneer catalogs.
- **Leaflet map with scoring markers:** Property map with color-coded markers by score, floating detail panel, and geographic filters. Reusable for any geo-enabled inventory display.
- **Client-side personalization system:** localStorage-based user profile with dynamic content reweighting. Reusable for any tool that adapts to user preferences without backend.

## Patterns That Map to kb/patterns/

- Public data ingestion and normalization (cross-reference: `kb/patterns/public-data-ingestion.md`)
- Geospatial intelligence dashboard (cross-reference: `kb/patterns/geospatial-intelligence.md`)
- Scoring engine (cross-reference: `kb/patterns/scoring-engine.md`)
- Zero-infrastructure data product (cross-reference: `kb/patterns/zero-infra-data-product.md`)

## Data Sources and Integrations

- **Caixa Economica Federal:** Daily CSV catalogs of properties for sale by state
- **Prefeitura de BH / ITBI:** Real estate transactions declared 2008-2026 with value, neighborhood, and typology
- **Google Maps API:** Street View, Places (nearby amenities), Directions (commute times)
- **URBEL:** Vila/favela registry for risk flagging (BH-specific)
- **Cartorio de RI:** Property registration data (variable access by state)
