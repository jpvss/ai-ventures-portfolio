---
title: "Kiiry CRM"
type: project
slug: kiiry-crm
vertical: adjacent
language: en
last_compiled: 2026-04-02
---

# Kiiry CRM

**Type:** SaaS / B2B Sales CRM

**Description:** B2B prospecting CRM with intelligent scoring for distributed solar energy sales.

## Problem It Solves

Solar energy sales teams spend hours manually searching for commercial leads and cannot prioritize which companies to approach first. Kiiry CRM automates lead capture via Google Places, classifies leads by energy potential and financial profile, and organizes the sales funnel in Kanban for 8+ simultaneous salespeople.

## Key Features

- Automatic lead import from Google Places API with intelligent deduplication and data enrichment (rating, reviews, phone, website)
- Multidimensional 0-100 scoring across 5 axes (energy potential, size, ICP fit, credibility, reachability) with automatic kWh consumption and monthly bill estimation by business type
- 8-stage Kanban pipeline with drag-ready cards, salesperson filter, quick stage advancement, and lost lead tracking with reason
- Automatic tariff group classification (A vs B) with confidence levels and financial viability analysis by voltage segment
- Team management with territories, activity leaderboard, conversion rate, and automatic detection of 68+ franchise/chain brands with headquarters data

## Tech Stack

| Technology | Role |
|---|---|
| Next.js 16 | Full-stack framework |
| React 19 | UI rendering |
| TypeScript | Type safety |
| Tailwind CSS v4 | Styling |
| shadcn/ui | Component library |
| Supabase | Database, auth, real-time |
| Google Places API (New) | Lead sourcing |
| Recharts | Data visualization |
| Lucide React | Icons |
| Vercel | Deployment |

## Capabilities Demonstrated

- Domain-specific scoring model with multiple weighted dimensions and sector-specific energy consumption estimates
- External API integration (Google Places) with transformation, deduplication, and data enrichment in automated pipeline
- Complete CRM with visual pipeline, multi-territory team management, and activity tracking — production-ready for 8+ users
- Brazilian regulatory financial analysis (CEMIG tariffs, A/B tariff groups, peak vs off-peak hours) applied to business decisions
- Automatic data pattern detection (chains/franchises, approach type, minimum viability) with domain-specific business rules

## Target Opportunities

| Segment | Project Type | Price Range | MVP Timeline |
|---|---|---|---|
| Energy / Utilities | Prospecting CRM with scoring for solar distributors or energy efficiency firms | R$ 30k-60k | 2-3 weeks |
| Real Estate / Construction | Prospecting CRM for condo and builder sales (solar, automation, security) | R$ 25k-45k | 3-4 weeks |
| Healthcare | Prospecting CRM for medical supply and equipment companies | R$ 35k-60k | 3-4 weeks |
| Food Service | Prospecting CRM for food/beverage distributors serving restaurants and bars | R$ 20k-40k | 2-3 weeks |

## Vertical Relevance

**Primary:** adjacent (solar energy sales, B2B CRM — not directly in core 4 verticals)

Cross-cutting relevance: The CRM pattern with domain-specific scoring is directly applicable to insurance-surety (broker CRM), mining (equipment/service sales CRM), and auctions (bidder management CRM).

## Links

- **Deploy:** https://kiiry-crm.vercel.app
- **Repository:** https://github.com/jpvss/kiiry-crm
