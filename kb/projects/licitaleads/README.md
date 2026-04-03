---
title: "LicitaLeads"
type: project
slug: licitaleads
vertical: insurance-surety
language: en
last_compiled: 2026-04-02
---

# LicitaLeads

**Type:** SaaS / Sales intelligence tool

**Description:** Commercial intelligence for surety bond brokers sourced from public procurement contracts.

## Problem It Solves

Surety bond brokers waste hours manually scouring the PNCP (National Public Procurement Portal) to find contracts that require guarantees. LicitaLeads ingests, enriches, and scores ~23K public contracts automatically, delivering prioritized leads with contact data and commission estimates.

## Key Features

- Contract ingestion pipeline from PNCP API with enrichment via BrasilAPI (CNPJ, phone, email, QSA) and ineligibility checks via CEIS/CNEP
- Composite score 0-100 with 4 dimensions (value, recency, contact, category) and A/B/C tier classification with guarantee estimate
- Dashboard with 11 combined filters (state, tier, value, period, CNAE, size, phase, contract type, category, contact, text search) and real-time KPIs
- Quick actions per lead: pre-filled WhatsApp, call, email, copy summary, direct links to PNCP and source system
- Interactive commission calculator with insurance rate and broker percentage sliders, CSV export with 31 columns

## Tech Stack

| Technology | Role |
|---|---|
| Next.js 16 | Full-stack framework |
| React 19 | UI rendering |
| TypeScript | Type safety |
| Tailwind CSS v4 | Styling |
| shadcn/ui | Component library |
| Zod 4 | Schema validation |
| Lucide React | Icons |
| Resend | Transactional email |
| tsx | TypeScript execution for scripts |
| Vercel | Deployment |

## Capabilities Demonstrated

- Ingestion and normalization of heterogeneous government data (PNCP, BrasilAPI, Portal da Transparencia) with idempotent pipeline and circuit breaker
- Domain-specific scoring with regulatory rule modeling for the Brazilian surety bond market (Lei 14.133, guarantee percentages by category)
- Automated business data enrichment (CNPJ to razao social, phone, email, QSA, CNAE, size, capital social) with rate limiting and resume-safety
- Data-driven B2B product with zero infrastructure (static JSON, no database, Vercel free tier) for rapid market validation
- High-density informational UI with composite filters, contextual actions, and structured export for sales workflow

## Target Opportunities

| Segment | Project Type | Price Range | MVP Timeline |
|---|---|---|---|
| Insurance / Brokers & insurers | Automated prospecting platform for corporate insurance brokers | R$ 25k-45k | 2-3 weeks |
| Government / GovTech | Public procurement intelligence dashboard for oversight agencies | R$ 40k-70k | 3-4 weeks |
| Construction / Mid-size builders | Public works bid opportunity radar | R$ 20k-40k | 2-3 weeks |
| Financial / Banks & factoring | Credit origination platform for government suppliers | R$ 35k-60k | 3-4 weeks |

## Vertical Relevance

**Primary:** insurance-surety (surety bond lead generation, Lei 14.133 compliance, guarantee estimation)

Also relevant to: auctions (public procurement data), adjacent (GovTech, construction bid monitoring)

## Links

- **Deploy:** https://licitaleads.vercel.app
- **Repository:** https://github.com/jpvss/licitaleads
