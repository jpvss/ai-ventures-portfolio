---
title: "DeixaComigo — Architecture"
type: project
slug: deixacomigo
language: en
last_compiled: 2026-04-02
---

# DeixaComigo — Technical Architecture

## Tech Stack Choices and Rationale

- **Next.js 16 + React 19:** Full-stack framework with Server Actions for form handling and API routes for FIPE integration. Server Components for SEO-optimized pages.
- **Supabase:** PostgreSQL database with RLS policies for data isolation, migrations for schema management, and storage for uploaded assets. Deployed in GRU1 (Sao Paulo) for low latency.
- **Zod 4:** End-to-end validation from form input to Server Action to database write. Ensures data quality throughout the funnel.
- **Resend:** Transactional email for instant broker notification when a lead is captured. Reliable delivery with tracking.
- **Anthropic SDK:** LLM integration for enhanced valuation insights and natural language report generation.
- **Vercel:** Deployment with edge functions and automatic HTTPS. Region-optimized for Brazilian users.

## Data Architecture

- **Primary source:** FIPE/Parallelum API v2 — vehicle reference prices by brand/model/year, updated monthly
- **Cache layer:** Supabase PostgreSQL caching FIPE responses to reduce API calls and improve response time
- **Lead storage:** Supabase with RLS policies — vehicle data, valuation results, contact info, timestamps
- **No batch pipeline:** All data is fetched and processed in real-time during user interaction

## Key Technical Patterns

- **Free tool to lead capture funnel:** Provide genuine value (valuation) before asking for contact — proven conversion pattern for B2B/B2C
- **API caching in database:** FIPE responses cached in Supabase with TTL — reduces external API dependency and cost
- **Server Actions with Zod validation:** Type-safe form handling from client to database with runtime validation at every boundary
- **Programmatic SEO:** Dynamic sitemap, structured data (Schema.org), and OpenGraph images generated per model/year — scales to hundreds of landing pages
- **Multi-factor pricing algorithm:** 6 calibrated factors with consignment aptitude classification — domain-specific pricing that goes beyond simple FIPE lookup

<!-- TO BE ENRICHED: Add learnings from project development -->

## Performance Considerations

- FIPE API cache in Supabase reduces external API calls and ensures fast valuations
- Server Components for SEO pages, Client Components only for interactive form
- Vercel edge deployment for low-latency Brazilian user access

<!-- TO BE ENRICHED: Add learnings from project development -->

## Deployment Architecture

- Vercel hosting with Server Actions and API routes
- Supabase hosted PostgreSQL (GRU1 region)
- Resend for email delivery
- No batch processing — all real-time

<!-- TO BE ENRICHED: Add learnings from project development -->
