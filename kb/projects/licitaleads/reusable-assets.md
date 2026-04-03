---
title: "LicitaLeads — Reusable Assets"
type: project
slug: licitaleads
language: en
last_compiled: 2026-04-02
---

# LicitaLeads — Reusable Assets

## Technical Components

- **PNCP ingestion pipeline:** Idempotent pipeline for ingesting public procurement data with circuit breaker and resume-safety. Directly applicable to any government data product.
- **CNPJ enrichment module:** Automated lookup of business data (razao social, phone, email, QSA, CNAE, porte, capital social) via BrasilAPI with rate limiting. Reusable for any Brazilian B2B product.
- **CEIS/CNEP compliance checker:** Ineligibility verification against Portal da Transparencia blacklists. Applicable to compliance/due diligence tools.
- **Composite scoring engine:** 4-dimension score (0-100) with tier classification (A/B/C) and guarantee estimation. Pattern reusable for any lead prioritization system.
- **Commission calculator component:** Interactive calculator with sliders for insurance rate and broker percentage. Adaptable for any commission-based sales tool.
- **High-density filter dashboard:** 11 combined filters with real-time KPIs — reusable UI pattern for data exploration.
- **Zero-infra data product architecture:** Static JSON + Vercel free tier pattern for rapid market validation without database costs.

## Patterns That Map to kb/patterns/

- Public data ingestion and normalization (cross-reference: `kb/patterns/public-data-ingestion.md`)
- CNPJ enrichment pipeline (cross-reference: `kb/patterns/cnpj-enrichment.md`)
- Lead scoring engine (cross-reference: `kb/patterns/scoring-engine.md`)
- Zero-infrastructure data product (cross-reference: `kb/patterns/zero-infra-data-product.md`)
- Compliance checking (cross-reference: `kb/patterns/compliance-automation.md`)

## Data Sources and Integrations

- **PNCP API:** National procurement portal — all public contracts, bids, and price registries
- **BrasilAPI:** CNPJ lookup for business enrichment — free tier with rate limits
- **Portal da Transparencia / CGU:** CEIS and CNEP ineligibility databases
- **SUSEP data:** Insurance market data for premium and claims analysis (referenced in opportunities)
