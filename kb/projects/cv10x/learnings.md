---
title: "CV10x — Learnings"
type: project
slug: cv10x
language: en
last_compiled: 2026-04-02
---

# CV10x — Learnings

## What Worked Well

- **Structured LLM output via Zod schemas** — Using Zod schemas to enforce structured Claude API responses (5-dimension scores, prioritized suggestions, section rewrites) eliminated free-form parsing and ensured consistent, programmatically consumable output across thousands of resume analyses.
- **Complete B2C conversion funnel** — The progression from free upload -> quick win -> email gate -> full report -> nurture sequence (E1-E5) -> Pro upsell -> Hotmart payment -> automatic delivery created a fully automated revenue pipeline with no manual intervention required.
- **GitHub Actions cron for nurture email sequence** — Running the 5-email nurture sequence as serverless cron jobs via GitHub Actions with Redis queue dedup avoided the cost and complexity of a dedicated email automation platform while maintaining reliable delivery scheduling.
- **Meta CAPI + Google Ads server-side tracking** — Implementing server-side conversion tracking for both Meta and Google provided accurate attribution data even with browser ad-blockers, enabling informed paid acquisition decisions.
- **Dynamic OG image generation** — Creating multiple OG image formats (landscape, portrait, story, square) via @vercel/og for social sharing turned each resume analysis into a shareable marketing asset, driving organic viral growth.

## Challenges Encountered

- **LLM output consistency at scale** — Despite Zod schema enforcement, Claude occasionally produces scoring that is too generous or suggestions that are too generic; iterative prompt engineering with system cache and temperature tuning was needed to achieve consistently useful output quality.
- **Hotmart webhook reliability** — Hotmart's payment webhook delivery is not always immediate or reliable; implementing idempotent webhook handlers with retry verification against Hotmart's API was necessary to prevent duplicate Pro report deliveries or missed payments.
- **Email deliverability for nurture sequence** — Resend's deliverability requires proper SPF/DKIM/DMARC configuration and warm-up; initial emails landed in spam for Gmail users until DNS records were properly configured and sending volume was gradually increased.
- **Rate limiting without user accounts** — Implementing IP-based rate limiting and monthly email limits without user authentication required balancing fraud prevention (multiple analyses from same IP) against legitimate use (shared office IPs, mobile networks with NAT).

## Key Technical Decisions

- **Next.js 15 + Vercel over a Python backend** — Chose Next.js for the full-stack framework despite the LLM integration being API-call-based, leveraging Vercel's edge functions for OG image generation, analytics, and serverless API routes — keeping the entire product in a single deployable unit.
- **Hotmart over Stripe for payments** — Selected Hotmart as the payment processor because it handles Brazilian payment methods (boleto, PIX, installment credit cards), tax invoicing (nota fiscal), and affiliate marketing infrastructure natively — critical for a B2C product targeting Brazilian professionals.
- **Upstash Redis for queue and caching** — Used Upstash's serverless Redis for the nurture email queue (with hash-based dedup) and analysis result caching, avoiding a persistent database while getting reliable queue semantics at serverless-compatible pricing.
- **SerpAPI for job matching** — Integrated SerpAPI for Pro users' automatic job matching rather than building a custom job scraper, trading API cost for reliability and breadth of job listing coverage — with heuristic pre-filtering before LLM ranking to control API costs.

## Business Impact

- **Proved AI-native B2C product viability** — CV10x demonstrated that an LLM-powered product can generate revenue through a freemium model with automated upsell, validating the pattern for future AI-native products across consulting verticals.
- **Built a complete marketing automation reference implementation** — The end-to-end system (cron nurture -> Redis queue -> Resend email -> Meta CAPI tracking -> Hotmart payment -> automatic delivery) serves as a reusable blueprint for any B2C product launch the agency undertakes for clients.
- **Validated Claude API for production workloads** — Running thousands of resume analyses through Claude with structured output, retry logic, and timeout handling demonstrated that the Anthropic API is production-ready for client-facing products — not just internal tools.
- **Generated portfolio credibility for AI consulting** — A live, revenue-generating AI product (cv10x.escoladados.com) provides stronger proof of AI integration capability than any case study or prototype, directly supporting the agency's positioning as an AI-native consultancy.
