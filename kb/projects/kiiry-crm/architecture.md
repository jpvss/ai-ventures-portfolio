---
title: "Kiiry CRM — Architecture"
type: project
slug: kiiry-crm
language: en
last_compiled: 2026-04-02
---

# Kiiry CRM — Technical Architecture

## Tech Stack Choices and Rationale

- **Next.js 16 + React 19:** Full-stack framework with Server Components for dashboard pages and Client Components for interactive Kanban pipeline.
- **Supabase:** PostgreSQL database with real-time subscriptions for multi-user CRM updates, authentication for team management, and RLS for data isolation between territories.
- **Google Places API (New):** Primary lead sourcing — search by business type and location, returning ratings, reviews, contact info. New API version for richer data and better pricing.
- **Recharts:** Lightweight charting for team leaderboards, conversion funnels, and scoring distribution visualizations.
- **shadcn/ui:** Consistent component library for CRM interface — tables, cards, dialogs, and Kanban board components.

## Data Architecture

- **Lead sourcing:** Google Places API -> deduplication -> enrichment -> scoring -> Supabase storage
- **CRM state:** Supabase PostgreSQL with real-time subscriptions for multi-user pipeline updates
- **Scoring:** Computed at import time and stored; re-computed on manual data updates
- **Team data:** User management with territory assignments and activity logging in Supabase

## Key Technical Patterns

- **API-sourced lead generation:** Google Places -> dedup -> enrich -> score pipeline. Reusable for any B2B prospecting product.
- **Multi-axis scoring with sector estimates:** 5-dimension scoring with energy consumption estimation by business type. Pattern for domain-specific lead qualification.
- **Kanban pipeline CRM:** 8-stage visual pipeline with drag-and-drop, lost reason tracking, and stage-based analytics.
- **Multi-territory team management:** Salesperson territory assignment with leaderboard and activity tracking.
- **Franchise/chain detection:** Automatic identification of 68+ known brands from Google Places data for headquarters routing.
- **Regulatory tariff classification:** A/B tariff group assignment with confidence levels based on business type and estimated consumption.

<!-- TO BE ENRICHED: Add learnings from project development -->

## Performance Considerations

- Supabase real-time for live pipeline updates across multiple simultaneous users
- Scoring computed at import time to avoid runtime computation during pipeline browsing
- Google Places API rate limiting managed server-side to stay within quotas

<!-- TO BE ENRICHED: Add learnings from project development -->

## Deployment Architecture

- Vercel hosting with Server Actions and API routes
- Supabase hosted PostgreSQL with real-time subscriptions
- Google Places API integration via server-side API routes

<!-- TO BE ENRICHED: Add learnings from project development -->
