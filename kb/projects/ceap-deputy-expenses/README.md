---
title: "CEAP Dashboard — Parliamentary Transparency"
type: project
slug: ceap-deputy-expenses
vertical: adjacent
language: en
last_compiled: 2026-04-02
---

# CEAP Dashboard — Parliamentary Transparency

**Type:** Dashboard de dados / Public transparency tool

**Description:** Interactive dashboard analyzing R$ 686M in parliamentary expenses with statistical anomaly detection.

## Problem It Solves

Citizens, journalists, and oversight agencies cannot cross-reference parliamentary expense data (CEAP) with budget amendments to identify suspicious patterns. The dashboard applies statistical methods (Benford, HHI, CNAE mismatch) on 660K+ transactions and delivers investigation-ready risk signals.

## Key Features

- Dashboard with overview of R$ 686M in expenses from 847 deputies with KPIs, filters, and ranking
- Individual deputy profile with Benford metrics, HHI, round values, and automatic red flags
- Supplier concentration analysis (HHI) by expense category with drill-down
- Investigative spotlight with CEAP x Amendments cross-reference (Operacao Overclean case with interactive pivot table)
- CNAE mismatch detection: companies receiving payments for services outside their registered economic activity
- Data pipeline with collection via Dados Abertos API, CNPJ enrichment via OpenCNPJ/BrasilAPI, and DuckDB storage
- Category-level expense analysis (vehicles, advertising, fuel) with statistical benchmarks

## Tech Stack

| Technology | Role |
|---|---|
| React 19 | UI rendering |
| TypeScript | Type safety |
| Vite | Build tool |
| Tailwind CSS v4 | Styling |
| D3.js | Statistical visualizations |
| React Router v7 | Client-side routing |
| TanStack React Query | Data fetching and caching |
| Zustand | State management |
| Supabase | Database and API |
| Cloudflare Pages | Static hosting |
| Cloudflare Workers | Serverless API functions |
| Python / pandas / scipy | Data pipeline and statistical analysis |
| DuckDB | Analytical queries |
| Jupyter Notebooks | Exploratory analysis |
| Playwright | E2E testing |

## Capabilities Demonstrated

- Massive ingestion of heterogeneous government data via public APIs with normalization, deduplication, and enrichment (CNPJ, CNAE, parliamentary names)
- Application of statistical fraud detection methods on real data (Benford's Law, HHI Index, round value analysis, economic activity mismatch)
- Cross-referencing databases with incompatible schemas using fuzzy name matching and identifier normalization
- Analytical dashboard with D3.js visualizations, feature flags for phased launch, lazy loading, and global CDN deployment
- Reproducible data pipeline: API collection -> DuckDB -> Python analysis -> static JSON -> React frontend — no backend server

## Target Opportunities

| Segment | Project Type | Price Range | MVP Timeline |
|---|---|---|---|
| Government / Courts of Audit | Automatic alert panel for expense and agreement auditing | R$ 50k-100k | 4-6 weeks |
| Journalism / Investigative media | Data investigation tool with alerts and publication-ready visualizations | R$ 30k-60k | 3-4 weeks |
| Compliance / Government contractors | Supplier due diligence and reputational risk monitoring dashboard | R$ 35k-70k | 3-5 weeks |
| Education / Data teaching platforms | Practical data analysis courses with real public transparency cases | R$ 20k-40k | 2-3 weeks |

## Vertical Relevance

**Primary:** adjacent (public transparency, government oversight — not directly in the 4 core verticals)

Cross-cutting relevance: Fraud detection patterns apply to insurance-surety (claims fraud), investment-advisory (portfolio monitoring), mining (CFEM royalty auditing)

## Links

- **Deploy:** https://ceap.escoladados.com
- **Repository:** https://github.com/jpvsalomao/CEAPDashboard
