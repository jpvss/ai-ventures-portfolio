---
title: "CEAP Dashboard — Reusable Assets"
type: project
slug: ceap-deputy-expenses
language: en
last_compiled: 2026-04-02
---

# CEAP Dashboard — Reusable Assets

## Technical Components

- **Statistical fraud detection suite:** Benford's Law analyzer, HHI concentration index calculator, round value detector, CNAE mismatch checker. Reusable for any financial anomaly detection (insurance claims, procurement fraud, tax audit).
- **Government API ingestion pipeline:** Collection from Dados Abertos API with pagination, deduplication, and enrichment. Reusable for any Brazilian government data product.
- **CNPJ enrichment with CNAE validation:** Supplier lookup with economic activity cross-validation. Reusable for compliance and due diligence tools.
- **Fuzzy matching reconciliation engine:** Cross-referencing databases with incompatible schemas via name normalization. Pattern for any multi-source data integration.
- **D3.js statistical visualization components:** Benford distribution chart, HHI bar chart, anomaly scatter plot. Reusable for analytical dashboards.
- **Feature flag system:** Progressive rollout of dashboard sections. Reusable for SaaS launch management.
- **Cloudflare Pages + Workers deployment:** Edge deployment pattern for global CDN hosting with serverless API. Reusable infrastructure pattern.

## Patterns That Map to kb/patterns/

- Public data ingestion and normalization (cross-reference: `kb/patterns/public-data-ingestion.md`)
- CNPJ enrichment pipeline (cross-reference: `kb/patterns/cnpj-enrichment.md`)
- Compliance automation / fraud detection (cross-reference: `kb/patterns/compliance-automation.md`)
- Scoring engine (cross-reference: `kb/patterns/scoring-engine.md`)

## Data Sources and Integrations

- **API Dados Abertos da Camara:** CEAP expenses, deputy profiles, propositions, votations
- **Portal da Transparencia:** Budget amendments, transfers, agreements (CSV, API)
- **OpenCNPJ / BrasilAPI:** Free CNPJ lookup with CNAE, QSA, cadastral status
- **CEIS/CNEP/CEPIM (CGU):** Ineligible and punished company registries
