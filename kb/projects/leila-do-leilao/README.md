---
title: "Leila do Leilao"
type: project
slug: leila-do-leilao
vertical: auctions
language: en
last_compiled: 2026-04-02
---

# Leila do Leilao

**Type:** Dashboard de dados / Real estate auction intelligence tool

**Description:** Intelligence for Caixa real estate auctions with true discount calculated via BH ITBI transaction data.

## Problem It Solves

Caixa real estate auction investors cannot tell if the advertised discount is real because Caixa's appraisal does not reflect market price. Leila cross-references real ITBI transaction data (2008-2026) with the Caixa catalog, revealing the true discount and scoring each property with a multidimensional Deal Score.

## Key Features

- Dashboard with KPIs, interactive filters by modality/city/price, and ranking of top 50 properties by Deal Score or discount
- Full property table for MG with 14 columns, 11 combined filters, investor-profile-customizable scoring, and CSV export
- Interactive Leaflet map with Deal Score markers, floating detail panel, sidebar listing, and geographic filters
- Complete financial simulator: ROI, SAC financing, municipality-specific ITBI, notary costs, cash flow, and maximum bid calculator via binary search
- Property detail page with Street View, nearby places (Google Places), commute times, neighborhood ITBI trend, and risk flags (lien, vilas/favelas URBEL)

## Tech Stack

| Technology | Role |
|---|---|
| Next.js 15 | Full-stack framework |
| React 19 | UI rendering |
| TypeScript | Type safety |
| Tailwind CSS v4 | Styling |
| Leaflet / React-Leaflet | Map rendering |
| DuckDB | Analytical queries |
| Python 3.10+ | Data pipeline |
| Pandas | Data manipulation |
| httpx | HTTP client for scraping |
| BeautifulSoup4 | HTML parsing |
| Pydantic v2 | Data validation |
| geopy | Geocoding |
| Google Maps API | Street View, Places, Directions |

## Capabilities Demonstrated

- Cross-referencing heterogeneous public datasets (Caixa CSV, municipal ITBI, detail page scraping) to generate insight no single source offers — true discount vs. market
- Domain-specific financial modeling with Brazilian real estate market rules (municipality-specific ITBI, SAC financing, FGTS, notary costs, auctioneer commission)
- Modular Python data pipeline with ingestion, enrichment, geocoding, and scoring — each module runs standalone, exports static JSON for frontend
- Interactive geospatial visualization with data classified by multidimensional scoring (discount, occupancy, modality, financing, data confidence)
- User profile personalization (budget, objective, risk tolerance) with dynamic score reweighting — no backend, all client-side via localStorage

## Target Opportunities

| Segment | Project Type | Price Range | MVP Timeline |
|---|---|---|---|
| Real Estate / Auction advisors | SaaS intelligence platform for auction advisory firms | R$ 25k-50k | 2-3 weeks |
| Financial / Mortgage fintechs | Automated collateral valuation engine for credit origination | R$ 40k-70k | 3-4 weeks |
| Government / Municipal finance | ITBI-based tax intelligence dashboard for municipalities | R$ 50k-90k | 3-4 weeks |
| Insurance / Property insurers | Transaction-data-based residential insurance pricing tool | R$ 35k-60k | 3-4 weeks |

## Vertical Relevance

**Primary:** auctions (real estate auction intelligence, Deal Score, bid optimization)

Also relevant to: investment-advisory (real estate investment analysis), insurance-surety (property valuation for insurance pricing)

## Links

- **Deploy:** Not deployed
- **Repository:** https://github.com/jpvss/Leila-do-leilao
