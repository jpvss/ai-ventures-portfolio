---
title: "CV10x"
type: project
slug: cv10x
vertical: adjacent
language: en
last_compiled: 2026-04-02
---

# CV10x

**Type:** SaaS / B2C digital product with infoproduct monetization

**Description:** AI-powered resume analyzer that scores, suggests improvements, and rewrites sections.

## Problem It Solves

Data professionals in Brazil do not know if their resume is competitive. They send applications and receive no responses without understanding why. CV10x analyzes the resume across 5 dimensions, shows exactly what to improve, and in the Pro plan rewrites each section with ready-to-copy alternatives.

## Key Features

- Resume upload (PDF/DOCX/TXT) with text extraction and AI Claude analysis across 5 dimensions (Technical, Impact, Structure, ATS, Narrative) with 0-100 score
- Free quick win with highest-impact immediate action, email gate for full report with 8-15 prioritized suggestions by dimension
- Paid Pro report (via Hotmart) with personalized section rewrites (A/B/C options), professional summary, ATS keyword analysis, interview prep, and action plan
- Automated nurture email sequence (E1-E5) with cron jobs via GitHub Actions, Redis queue with dedup, and conversion tracking per stage
- Automatic job matching for Pro users: job search via SerpAPI, heuristic pre-filter, and LLM ranking with categories (highlight/fit/next step)

## Tech Stack

| Technology | Role |
|---|---|
| Next.js 15 | Full-stack framework |
| React 18 | UI rendering |
| TypeScript | Type safety |
| Tailwind CSS | Styling |
| Anthropic Claude API | LLM analysis and rewriting |
| Zod | Validation |
| Upstash Redis | Queue and caching |
| Resend | Transactional and nurture email |
| @vercel/og | Dynamic OG image generation |
| @vercel/analytics | Usage analytics |
| Framer Motion | Animations |
| Hotmart | Payment processing |
| Meta CAPI | Server-side conversion tracking |
| Google Ads | Paid acquisition tracking |
| GitHub Actions | Cron jobs for nurture sequence |
| Vercel | Deployment |

## Capabilities Demonstrated

- Advanced LLM integration (Claude) with structured output via Zod schemas, iterative prompt engineering with system cache, retries, and production timeout handling
- Complete B2C product architecture with conversion funnel: free tier -> email gate -> nurture sequence -> Pro upsell -> payment (Hotmart webhook) -> automatic delivery
- End-to-end marketing automation system: serverless cron jobs (GitHub Actions), Redis nurture queue with hash dedup, batch email via Resend, server-side tracking (Meta CAPI + Google Ads), UTM attribution
- Dynamic OG image generation via @vercel/og with multiple formats (landscape, portrait, story, square) for social media sharing
- Production digital product operation with IP rate limiting, monthly email limits, retry queues for failures, idempotency, and observability via Vercel runtime logs

## Target Opportunities

| Segment | Project Type | Price Range | MVP Timeline |
|---|---|---|---|
| HR / Outplacement consultancies | White-label resume analysis platform for career firms | R$ 25k-45k | 2-3 weeks |
| Education / EdTechs & bootcamps | Employability module integrated with LMS platforms | R$ 30k-55k | 3-4 weeks |
| Recruiting / HRTechs & ATS platforms | Resume scoring and screening API for recruitment platforms | R$ 35k-65k | 3-4 weeks |
| Government / Public employment programs | Professional diagnostic tool for SINE/PAT employment agencies | R$ 40k-80k | 4-5 weeks |

## Vertical Relevance

**Primary:** adjacent (HR/career tech — not in core 4 verticals)

Cross-cutting relevance: The LLM integration patterns, B2C funnel architecture, and marketing automation system are reusable across all verticals for client-facing products.

## Links

- **Deploy:** https://cv10x.escoladados.com
- **Repository:** https://github.com/jpvss/CV10x
