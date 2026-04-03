---
title: "DeixaComigo"
type: project
slug: deixacomigo
vertical: adjacent
language: en
last_compiled: 2026-04-02
---

# DeixaComigo

**Type:** Lead generation tool / Vertical automotive SaaS

**Description:** Vehicle valuation tool that converts car owners into consignment clients.

## Problem It Solves

Owners of premium used cars (R$ 60-120K+) are lowballed by dealers who pay 75-85% of FIPE. DeixaComigo shows the concrete difference between selling to a dealer and consigning — with real-time FIPE data — and automatically captures the seller's lead for the consignment broker.

## Key Features

- Vehicle valuation engine with FIPE integration (Parallelum v2) and Supabase caching, comparing dealer estimate vs. market value vs. net consignment value with price ranges
- Pricing algorithm with 6 calibrated factors (brand, age, km, condition, regional demand, commission) and consignment aptitude classification (ideal/viable/marginal)
- Mobile-first form with cascading brand -> model -> year selection via FIPE API, formatted km input, and condition selection with explanatory micro-copy
- Lead capture integrated with valuation result, persisted in Supabase with email notification (Resend) to broker containing vehicle data and complete valuation
- Complete technical SEO: dynamic sitemap.xml, robots.txt, JSX-generated OpenGraph image, Schema.org WebApplication, meta tags, and canonical URLs

## Tech Stack

| Technology | Role |
|---|---|
| Next.js 16 | Full-stack framework |
| React 19 | UI rendering |
| TypeScript | Type safety |
| Supabase | Database, auth, storage |
| Tailwind CSS v4 | Styling |
| shadcn/ui | Component library |
| Zod 4 | Validation |
| Resend | Transactional email |
| Anthropic SDK | LLM integration |
| Lucide React | Icons |
| Sonner | Toast notifications |
| Vercel | Deployment |

## Capabilities Demonstrated

- Domain-specific pricing model with multiple calibrated factors (FIPE table, dealer spreads, brand/age/km depreciation) and guard rails against overpromising
- External API integration (FIPE/Parallelum) with intelligent database cache layer, graceful fallback, and data validation
- Complete conversion funnel — from free value tool to qualified lead capture with automatic notification — implemented as Server Actions with Zod validation
- Real product infrastructure with Supabase (PostgreSQL + RLS policies + migrations), authentication, transactional email (Resend), and GRU1 (Sao Paulo) region deployment
- Programmatic technical SEO for organic traffic generation at scale: sitemap, robots, structured data, dynamic OpenGraph, architecture ready for hundreds of model/year pages

## Target Opportunities

| Segment | Project Type | Price Range | MVP Timeline |
|---|---|---|---|
| Automotive / Dealerships | White-label valuation and vehicle capture tool | R$ 20k-40k | 2-3 weeks |
| Insurance / Auto insurance brokers | Auto insurance calculator with lead capture and integrated CRM | R$ 25k-50k | 3-4 weeks |
| Financial / Vehicle-backed credit fintechs | Vehicle collateral valuation engine for credit platforms | R$ 30k-55k | 2-3 weeks |
| Real Estate / Real estate agencies | Property valuation tool with lead capture for agencies | R$ 25k-50k | 3-4 weeks |

## Vertical Relevance

**Primary:** adjacent (automotive vertical, not in core 4)

Cross-cutting relevance: insurance-surety (auto insurance lead generation, SUSEP data integration), investment-advisory (vehicle-backed credit valuation)

## Links

- **Deploy:** https://deixacomigo.app
- **Repository:** https://github.com/jpvss/DeixaComigo
