---
title: "FloridaFlip"
type: project
slug: florida-flip
vertical: investment-advisory
language: en
last_compiled: 2026-04-02
---

# FloridaFlip

**Type:** Dashboard de dados / Ferramenta de inteligencia de mercado

**Description:** Real estate intelligence for investors in the Florida market with 2.1M+ properties.

## Problem It Solves

Real estate investors waste hours cross-referencing dozens of public data sources to find good opportunities. FloridaFlip aggregates everything — assessments, sales, rentals, flood risk, insurance — into a single panel with automatic opportunity signals.

## Key Features

- Interactive map of 67 counties with choropleth by metric (price, inventory, days on market)
- Search across 2.1M properties via DuckDB/Parquet with filters and automatic signals (high yield, below assessed, 70% rule)
- Flip/hold/BRRRR calculator with closing costs and insurance specific to Florida legislation
- Multidimensional submarket scoring by ZIP code (9 dimensions: vacancy, tenant quality, yield, risk)
- Executive dashboard with KPIs, trends, county comparison, and PDF report generation

## Tech Stack

| Technology | Role |
|---|---|
| Next.js 16 | Full-stack framework |
| React 19 | UI rendering |
| TypeScript | Type safety |
| DuckDB | Analytical queries on millions of records (browser + server) |
| Apache Parquet | Columnar storage for property data |
| Google Maps API | Geospatial visualization |
| Tailwind CSS v4 | Styling |
| shadcn/ui | Component library |
| Recharts | Data visualization |
| jsPDF | PDF report generation |
| Python | Data pipeline / ingestion |
| Vercel | Deployment |

## Capabilities Demonstrated

- Ingestion and normalization of heterogeneous public data (FDOR, FEMA, Census ACS, Redfin) in reproducible Python pipeline
- Analytical queries over millions of records in-browser and server-side using DuckDB + Parquet with no external database
- Domain-specific financial modeling with local regulatory rules (FL insurance, OIR closing costs, NFIP)
- Interactive geospatial visualization with polygons, choropleth, and drill-down by region
- Multidimensional scoring with configurable weights for ranking and decision-making

## Target Opportunities

| Segment | Project Type | Price Range | MVP Timeline |
|---|---|---|---|
| Real Estate / Developers | Territorial intelligence panel for land prospecting | R$ 40k-80k | 3-4 weeks |
| Financial / Credit Fintechs | Geographic risk dashboard for mortgage origination | R$ 35k-60k | 3-4 weeks |
| Agribusiness / Land Funds | Rural property evaluation and comparison platform | R$ 50k-90k | 4-5 weeks |
| Retail / Expanding Chains | Geo-expansion tool for new store openings | R$ 30k-60k | 3-4 weeks |

## Vertical Relevance

**Primary:** investment-advisory (real estate investment intelligence, scoring, financial modeling)

Also relevant to: insurance-surety (flood risk, insurance cost modeling), adjacent (retail geo-expansion, agribusiness land evaluation)

## Links

- **Deploy:** https://florida-flip.vercel.app
- **Repository:** https://github.com/jpvss/florida-flip
