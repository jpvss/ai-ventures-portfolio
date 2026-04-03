---
title: "CV10x — Reusable Assets"
type: project
slug: cv10x
language: en
last_compiled: 2026-04-02
---

# CV10x — Reusable Assets

## Technical Components

- **LLM structured output pipeline:** Claude API integration with Zod schema validation for type-safe, parseable AI outputs. System prompt caching, retries, and timeout handling. Reusable for any LLM-powered analysis product.
- **Email-gated conversion funnel:** Free value -> email capture -> nurture sequence -> paid upsell pattern. Complete implementation with rate limiting and dedup. Reusable for any B2C SaaS.
- **Serverless nurture email system:** GitHub Actions cron -> Redis queue -> Resend batch email with dedup, tracking, and conversion attribution. Reusable marketing automation pattern.
- **Server-side conversion tracking:** Meta CAPI + Google Ads server events implementation. Reusable for any paid acquisition funnel.
- **Dynamic OG image generator:** @vercel/og with multiple format templates (landscape, portrait, story, square). Reusable for any product requiring social share cards.
- **Hotmart payment webhook integration:** Brazilian payment processing with automatic Pro delivery on payment confirmation. Reusable for any infoproduct or SaaS with Brazilian payment methods.
- **Rate limiting system:** IP-based rate limiting + monthly email caps with Redis counters. Reusable for any public-facing API.

## Patterns That Map to kb/patterns/

- LLM integration and structured output (cross-reference: `kb/patterns/llm-integration.md`)
- Lead generation funnel (cross-reference: `kb/patterns/lead-generation-funnel.md`)
- Marketing automation (cross-reference: `kb/patterns/marketing-automation.md`)
- Programmatic SEO (cross-reference: `kb/patterns/programmatic-seo.md`)

## Data Sources and Integrations

- **Anthropic Claude API:** Core analysis engine for resume evaluation and rewriting
- **SerpAPI:** Job search for Pro user matching feature
- **FIPE / job portals:** Referenced in opportunity analysis for market data
- **Upstash Redis:** Serverless queue and caching infrastructure
- **Resend:** Transactional and batch email delivery
- **Hotmart:** Brazilian payment gateway with webhook integration
- **Meta CAPI / Google Ads:** Server-side conversion tracking APIs
