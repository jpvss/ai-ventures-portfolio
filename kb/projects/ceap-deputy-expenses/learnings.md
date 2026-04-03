---
title: "CEAP Dashboard — Learnings"
type: project
slug: ceap-deputy-expenses
language: en
last_compiled: 2026-04-02
---

# CEAP Dashboard — Learnings

## What Worked Well

- **Statistical fraud detection on real government data** — Applying Benford's Law, HHI supplier concentration, round value analysis, and CNAE mismatch detection on 660K+ CEAP transactions totaling R$ 686M from 847 deputies produced actionable anomaly signals that journalists and oversight bodies can investigate directly.
- **D3.js custom visualizations** — Building statistical visualizations (Benford digit distribution charts, HHI concentration heatmaps, expense category breakdowns) with D3.js rather than a charting library delivered publication-quality graphics suited for investigative journalism output.
- **CNPJ enrichment pipeline** — Enriching supplier CNPJs via OpenCNPJ and BrasilAPI to retrieve CNAE codes, company names, and registration data enabled CNAE mismatch detection — identifying companies receiving payments for services outside their registered economic activity.
- **Static JSON architecture with CDN deployment** — The pipeline (API collection -> DuckDB -> Python analysis -> static JSON -> React frontend) eliminated backend server costs entirely, deploying to Cloudflare Pages with global CDN for sub-100ms response times.
- **Feature flags for phased launch** — Implementing feature flags enabled incremental rollout of investigation modules (Operacao Overclean cross-reference, CNAE mismatch) without redeploying or risking incomplete features in production.

## Challenges Encountered

- **Cross-referencing CEAP with budget amendments** — Amendments and CEAP expense databases use incompatible schemas with no shared identifiers; linking required fuzzy name matching on parliamentary names and approximate date/value matching, producing probabilistic rather than deterministic links.
- **Dados Abertos API rate limits and data gaps** — The Brazilian government open data API enforces rate limits and occasionally returns incomplete datasets for historical periods, requiring incremental collection with checkpoint resume and data completeness validation.
- **CNPJ data freshness** — OpenCNPJ and BrasilAPI reflect Receita Federal data with variable lag; some supplier CNPJs return outdated CNAE codes or "not found" results for recently registered companies, requiring fallback logic and confidence scoring.
- **Deputy name normalization** — Parliamentary names appear differently across data sources (full name, parliamentary name, name with/without accents, abbreviations), requiring a normalization layer with accent removal, alias mapping, and fuzzy matching to achieve cross-source linkage.

## Key Technical Decisions

- **React + Vite + Cloudflare Pages over Next.js** — Chose a pure SPA architecture over SSR because the entire dataset is pre-computed static JSON with no user-specific data, making server-side rendering unnecessary and enabling zero-cost hosting on Cloudflare Pages with Workers for lightweight API functions.
- **DuckDB for analytical pipeline over pandas-only** — Used DuckDB for complex aggregations (per-deputy statistics, category-level benchmarks, temporal trends) that would be slow or memory-intensive in pure pandas, while keeping pandas for data cleaning and transformation tasks where its API is more ergonomic.
- **Supabase for structured data storage** — Used Supabase as a persistent layer for enriched CNPJ data and computed anomaly scores, enabling the Cloudflare Workers API to serve dynamic queries without re-running the full analysis pipeline.
- **TanStack React Query + Zustand for state management** — Combined React Query for server state (API data fetching, caching, pagination) with Zustand for client state (filters, selected deputy, active tab), keeping concerns cleanly separated in a complex multi-view dashboard.

## Business Impact

- **Demonstrated fraud detection as a cross-vertical capability** — The statistical methods applied to parliamentary expenses (Benford, HHI, activity mismatch) are directly transferable to insurance claims fraud, mining royalty auditing, and investment portfolio monitoring — positioning the agency for compliance and audit engagements across all 4 verticals.
- **Built a public reference project** — Deployed at ceap.escoladados.com, the dashboard serves as a live portfolio piece demonstrating data engineering, statistical analysis, and visualization capabilities to prospective clients — more compelling than slide decks.
- **Validated the investigative journalism market** — Interest from journalists and civic tech organizations confirmed demand for data investigation tools at R$ 30k-60k per engagement, with potential for ongoing subscription models for automated alert systems.
- **Proved government data pipeline patterns** — The collection, enrichment, and analysis pipeline for Dados Abertos API data is reusable for any Brazilian government transparency dataset (TCU, CGU, Portal da Transparencia), establishing a foundation for government-sector consulting.
