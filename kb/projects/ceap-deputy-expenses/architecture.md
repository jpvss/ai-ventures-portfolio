---
title: "CEAP Dashboard — Architecture"
type: project
slug: ceap-deputy-expenses
language: en
last_compiled: 2026-04-02
---

# CEAP Dashboard — Technical Architecture

## Tech Stack Choices and Rationale

- **React 19 + Vite (no Next.js):** Client-side SPA for a data visualization-heavy dashboard. Vite for fast builds and HMR during development. No SSR needed since data is pre-processed.
- **D3.js:** Custom statistical visualizations (Benford distribution, HHI charts, anomaly scatter plots) requiring fine-grained control beyond charting libraries.
- **TanStack React Query:** Data fetching with caching, background refetching, and optimistic updates for dashboard interactions.
- **Zustand:** Lightweight state management for filter state, selected deputy, and dashboard configuration.
- **Supabase:** PostgreSQL database for structured storage of enriched expense data, CNPJ records, and amendment cross-references.
- **Cloudflare Pages + Workers:** Global CDN for static assets and serverless API functions for database queries — low-latency worldwide.
- **Python / pandas / scipy:** Statistical analysis pipeline — Benford's Law calculation, HHI computation, anomaly detection algorithms.
- **DuckDB + Jupyter Notebooks:** Exploratory analysis and data pipeline development before production deployment.
- **Playwright:** E2E testing for critical dashboard flows and data visualization correctness.

## Data Architecture

- **Primary source:** API Dados Abertos da Camara — CEAP expenses, deputy profiles, propositions
- **Enrichment:** OpenCNPJ/BrasilAPI for supplier CNPJ data (CNAE, razao social, QSA)
- **Cross-reference:** Portal da Transparencia for budget amendments (emendas) — fuzzy matching on parliamentary names
- **Storage:** Supabase PostgreSQL for structured query access; DuckDB for pipeline processing
- **Frontend data:** Mix of Supabase queries (via Cloudflare Workers) and pre-computed static JSON

## Key Technical Patterns

- **Statistical fraud detection:** Benford's Law, HHI concentration index, round value analysis, CNAE mismatch — applicable to any financial anomaly detection
- **Fuzzy matching for schema reconciliation:** Cross-referencing databases with incompatible schemas using name normalization and fuzzy matching
- **Feature flags for phased launch:** Progressive rollout of dashboard sections — pattern for SaaS launch management
- **Hybrid data serving:** Supabase for dynamic queries + static JSON for pre-computed aggregates — balances flexibility with performance
- **Cloudflare edge deployment:** Pages for static assets + Workers for API — zero cold-start serverless

<!-- TO BE ENRICHED: Add learnings from project development -->

## Performance Considerations

- Cloudflare global CDN for sub-100ms static asset delivery
- TanStack Query caching eliminates redundant API calls during dashboard exploration
- Lazy loading of heavy D3 visualizations
- Pre-computed aggregates in static JSON for instant KPI rendering

<!-- TO BE ENRICHED: Add learnings from project development -->

## Deployment Architecture

- Cloudflare Pages for static React build
- Cloudflare Workers for serverless API endpoints
- Supabase hosted PostgreSQL for structured data
- Python pipeline runs in CI/local for data refresh

<!-- TO BE ENRICHED: Add learnings from project development -->
