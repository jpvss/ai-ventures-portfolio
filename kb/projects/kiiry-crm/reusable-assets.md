---
title: "Kiiry CRM — Reusable Assets"
type: project
slug: kiiry-crm
language: en
last_compiled: 2026-04-02
---

# Kiiry CRM — Reusable Assets

## Technical Components

- **Google Places lead import pipeline:** API search -> deduplication -> enrichment -> scoring pipeline. Reusable for any B2B prospecting product targeting physical businesses.
- **Multi-axis lead scoring engine:** 5-dimension scoring (0-100) with sector-specific estimates. Reusable for any domain requiring lead qualification.
- **Kanban CRM pipeline:** 8-stage visual pipeline with drag-and-drop, lost reason tracking, and conversion analytics. Reusable CRM pattern for any sales team.
- **Multi-territory team management:** Salesperson assignment, territory management, leaderboard, and activity tracking. Reusable for any field sales operation.
- **Franchise/chain brand detector:** Automatic identification of 68+ known brands from business name matching. Reusable for any B2B product dealing with commercial establishments.
- **Tariff group classifier:** A/B tariff group classification with confidence levels based on business type and estimated consumption. Reusable for energy sector products.
- **Supabase real-time CRM:** Multi-user real-time pipeline updates with RLS data isolation. Reusable architecture for any collaborative CRM.

## Patterns That Map to kb/patterns/

- Scoring engine (cross-reference: `kb/patterns/scoring-engine.md`)
- Lead generation funnel (cross-reference: `kb/patterns/lead-generation-funnel.md`)
- Regulatory modeling (cross-reference: `kb/patterns/regulatory-modeling.md`)
- API caching and integration (cross-reference: `kb/patterns/api-caching.md`)

## Data Sources and Integrations

- **Google Places API (New):** Business establishment data with ratings, reviews, phone, website — primary lead source
- **ANEEL/SIGA:** Solar generation system registry — all registered GD plants in Brazil
- **CEMIG / distribuidoras:** Tariff data by group (B1, B2, B3, A3, A4) for financial viability assessment
- **Receita Federal:** CNPJ validation for company data enrichment
- **Supabase:** PostgreSQL with real-time subscriptions and RLS
