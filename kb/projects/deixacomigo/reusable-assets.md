---
title: "DeixaComigo — Reusable Assets"
type: project
slug: deixacomigo
language: en
last_compiled: 2026-04-02
---

# DeixaComigo — Reusable Assets

## Technical Components

- **FIPE API integration with cache:** Vehicle reference price lookup with Supabase cache layer, graceful fallback, and data validation. Reusable for any automotive product.
- **Multi-factor pricing engine:** 6-factor pricing algorithm with aptitude classification. Pattern for any domain-specific valuation tool (vehicles, properties, equipment).
- **Free tool to lead capture funnel:** Complete conversion funnel pattern — value delivery -> contact capture -> broker notification. Reusable for any professional service lead generation.
- **Server Actions + Zod validation pipeline:** Type-safe form-to-database flow with runtime validation. Reusable Next.js pattern for any data capture application.
- **Programmatic SEO infrastructure:** Dynamic sitemap, robots.txt, Schema.org, OpenGraph image generation. Reusable for any content-at-scale SEO strategy.
- **Supabase RLS + migrations pattern:** Database with row-level security policies and schema migrations. Reusable for any multi-tenant or data-sensitive application.
- **Email notification system:** Resend integration for transactional email with structured data payload. Reusable for any lead notification or alert system.

## Patterns That Map to kb/patterns/

- Lead generation funnel (cross-reference: `kb/patterns/lead-generation-funnel.md`)
- API caching and fallback (cross-reference: `kb/patterns/api-caching.md`)
- Scoring engine / pricing model (cross-reference: `kb/patterns/scoring-engine.md`)
- Programmatic SEO (cross-reference: `kb/patterns/programmatic-seo.md`)

## Data Sources and Integrations

- **FIPE / Parallelum API v2:** Vehicle reference prices by brand/model/year — updated monthly
- **DENATRAN/SENATRAN:** Vehicle registration data by municipality (aggregated public data)
- **Supabase PostgreSQL:** Lead storage with RLS policies
- **Resend:** Transactional email delivery
- **SUSEP/SES:** Auto insurance premium data by model and region (referenced in opportunities)
