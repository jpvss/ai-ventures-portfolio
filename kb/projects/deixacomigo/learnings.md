---
title: "DeixaComigo — Learnings"
type: project
slug: deixacomigo
language: en
last_compiled: 2026-04-02
---

# DeixaComigo — Learnings

## What Worked Well

- **FIPE API integration with Supabase caching** — Integrating with the Parallelum v2 FIPE API for real-time vehicle pricing while caching results in Supabase eliminated redundant API calls, ensured consistent pricing within sessions, and provided graceful fallback when the upstream API is unavailable.
- **6-factor pricing algorithm with consignment aptitude classification** — Calibrating the valuation model across brand, age, km, condition, regional demand, and commission percentage — then classifying vehicles as ideal/viable/marginal for consignment — delivered specific, actionable guidance rather than generic price ranges.
- **Complete conversion funnel as Server Actions** — Implementing the entire flow (vehicle selection -> valuation display -> lead capture -> email notification to broker) as Next.js Server Actions with Zod validation produced a clean, secure architecture with no exposed API endpoints.
- **Programmatic SEO infrastructure** — Dynamic sitemap.xml, robots.txt, Schema.org WebApplication markup, JSX-generated OpenGraph images, and canonical URLs created a foundation for organic traffic generation at scale — architecture ready for hundreds of model/year landing pages.
- **Mobile-first cascading form UX** — The brand -> model -> year cascading selection with formatted km input and condition micro-copy provided a frictionless mobile experience optimized for the target user (car owner researching on their phone).

## Challenges Encountered

- **FIPE API inconsistencies** — The Parallelum v2 API occasionally returns stale or inconsistent pricing data for recent model years, and the brand/model taxonomy changes between API versions, requiring defensive parsing and validation against known price ranges.
- **Consignment margin calibration** — Determining realistic dealer buy vs. consignment net margins required market research with actual consignment brokers; initial estimates were too optimistic, risking user trust if the tool overpromised net values.
- **Lead quality vs. volume trade-off** — Capturing leads too early in the funnel (before showing the valuation) increased drop-off; showing the full valuation before capture reduced lead volume but improved lead quality — the final design gates the full comparison at email capture.
- **Regional demand factor accuracy** — Vehicle demand varies significantly by Brazilian region (SUVs in rural areas vs. compact cars in Sao Paulo), but FIPE provides national pricing; the regional adjustment factor is an approximation that requires periodic recalibration.

## Key Technical Decisions

- **Next.js 16 + Supabase over a lightweight backend** — Chose Next.js with Supabase (PostgreSQL + RLS + auth) over a simpler backend because the project needed persistent lead storage, row-level security for multi-broker scenarios, and transactional email (Resend) — all available through Supabase's integrated ecosystem.
- **Zod 4 for end-to-end validation** — Used Zod schemas shared between client form validation and Server Action input validation, ensuring type safety across the full request lifecycle and preventing malformed data from reaching the pricing algorithm.
- **Resend for transactional email** — Chose Resend over SendGrid/SES for its developer-friendly API, React Email template support, and simple pricing model — appropriate for a low-volume lead notification use case where deliverability matters more than throughput.
- **Anthropic SDK integration** — Included LLM capability for potential natural-language vehicle description analysis and conversational lead qualification, demonstrating AI-native product architecture even in a traditional lead-gen tool.

## Business Impact

- **Proved the "valuation tool as lead magnet" pattern** — Demonstrated that a free valuation tool (vehicle, property, insurance) can generate qualified leads at near-zero marginal cost, with the valuation itself serving as both user value and sales qualification — applicable across automotive, real estate, and insurance verticals.
- **Validated white-label potential** — The tool's architecture (configurable branding, Supabase multi-tenancy, broker-specific email routing) is ready for white-label deployment to multiple consignment brokers at R$ 20k-40k per instance.
- **Built reusable lead capture infrastructure** — The Server Actions + Zod + Supabase + Resend lead capture pipeline is directly portable to any vertical where a free tool generates qualified leads (insurance quoting, property valuation, credit pre-qualification).
- **Established SEO-first product architecture** — The programmatic SEO infrastructure (dynamic pages per model/year, structured data, OG images) demonstrates a scalable organic acquisition strategy reusable for any product with a large taxonomy of searchable entities.
