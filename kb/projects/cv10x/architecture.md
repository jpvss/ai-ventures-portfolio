---
title: "CV10x — Architecture"
type: project
slug: cv10x
language: en
last_compiled: 2026-04-02
---

# CV10x — Technical Architecture

## Tech Stack Choices and Rationale

- **Next.js 15 + React 18:** Full-stack framework with API routes for LLM calls, Server Components for SEO pages, and client-side interactivity for upload/results UX.
- **Anthropic Claude API:** Core analysis engine — structured output with Zod schemas for reliable, parseable resume analysis. System prompt caching for cost optimization.
- **Upstash Redis:** Serverless Redis for nurture email queue with dedup (hash-based), rate limiting counters, and session caching. Zero-ops on Vercel.
- **Resend:** Transactional email for both immediate results delivery and multi-step nurture sequence (E1-E5).
- **Hotmart:** Payment processing for Pro plan — webhook-based delivery trigger. Brazilian payment provider with PIX, boleto, and credit card support.
- **GitHub Actions:** Cron jobs for nurture email processing — runs every N hours, pulls from Redis queue, sends via Resend.
- **Meta CAPI + Google Ads:** Server-side conversion tracking for accurate attribution — not dependent on client-side cookies.
- **@vercel/og:** Dynamic OG image generation for social sharing — creates score-based share cards per analysis.
- **Framer Motion:** Smooth animations for score reveal and result transitions.

## Data Architecture

- **Input:** Resume files (PDF/DOCX/TXT) -> text extraction -> Claude analysis
- **Analysis storage:** Results stored in Redis with TTL — ephemeral by design
- **Lead storage:** Email + analysis metadata in Redis for nurture queue
- **Payment:** Hotmart webhook triggers Pro report generation and delivery
- **No traditional database:** All state managed via Redis (Upstash) — fully serverless

## Key Technical Patterns

- **LLM structured output:** Zod schemas define expected Claude response format — ensures parseable, type-safe analysis results
- **Email-gated conversion funnel:** Free quick win -> email capture -> full report -> nurture -> Pro upsell. Proven B2C SaaS pattern.
- **Serverless cron via GitHub Actions:** Schedule-triggered workflows that process Redis queues — no server infrastructure
- **Server-side conversion tracking:** Meta CAPI and Google Ads server events for cookie-independent attribution
- **Idempotent operations:** Hash-based dedup in Redis prevents duplicate emails and analyses
- **Rate limiting:** IP-based rate limiting and monthly email caps to prevent abuse

<!-- TO BE ENRICHED: Add learnings from project development -->

## Performance Considerations

- Claude API calls with system prompt caching reduce latency and cost for repeated analyses
- Redis caching for intermediate results
- OG image generation at build time where possible, on-demand for dynamic scores

<!-- TO BE ENRICHED: Add learnings from project development -->

## Deployment Architecture

- Vercel hosting with API routes and Server Actions
- Upstash Redis (serverless, multi-region)
- GitHub Actions for scheduled nurture processing
- Hotmart for payment processing (webhook integration)

<!-- TO BE ENRICHED: Add learnings from project development -->
