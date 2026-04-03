---
title: "Kiiry CRM — Learnings"
type: project
slug: kiiry-crm
language: en
last_compiled: 2026-04-02
---

# Kiiry CRM — Learnings

## What Worked Well

- **Google Places API for automated lead sourcing** — Importing commercial leads directly from Google Places with intelligent deduplication and enrichment (rating, reviews, phone, website) eliminated manual prospecting and provided a scalable lead generation pipeline that sales teams of 8+ can share.
- **5-axis scoring model with energy consumption estimation** — Scoring leads across energy potential, size, ICP fit, credibility, and reachability — with automatic kWh consumption and monthly bill estimation by business type — gave salespeople a data-driven prioritization system that replaced gut-feel lead selection.
- **8-stage Kanban pipeline with drag-ready cards** — A visual pipeline with salesperson filtering, quick stage advancement, and lost lead tracking with reason provided the sales team an intuitive workflow that mirrors their actual process without requiring training on complex CRM software.
- **Automatic tariff group classification (A vs. B)** — Classifying leads into CEMIG tariff groups with confidence levels and financial viability analysis by voltage segment enabled sales reps to identify high-value prospects (Group A with higher savings potential) before the first contact.
- **Franchise/chain detection for 68+ brands** — Automatically identifying franchise and chain locations (with headquarters data) from Google Places results prevented wasted outreach to locations without local decision-making authority on energy contracts.

## Challenges Encountered

- **Google Places API cost management** — The new Google Places API charges per request with different pricing tiers per field; retrieving full enrichment data (photos, reviews, opening hours) for bulk imports required careful field selection to keep API costs within budget for a solar startup.
- **Energy consumption estimation accuracy** — Estimating kWh consumption by business type (restaurant vs. office vs. retail) relies on industry benchmarks that vary significantly by establishment size, equipment, and region — the estimates are directional indicators, not precise measurements.
- **Multi-territory team coordination** — Supporting 8+ simultaneous salespeople with territory assignments required conflict detection (two reps claiming the same lead) and activity attribution that simple Kanban boards do not natively provide.
- **Lead data decay** — Google Places data (phone numbers, opening hours, even business existence) changes frequently; leads imported weeks ago may have stale contact information, requiring periodic re-validation that adds pipeline complexity.

## Key Technical Decisions

- **Next.js 16 + Supabase over a traditional CRM platform** — Built a custom CRM rather than customizing Salesforce/HubSpot because the core value is in the domain-specific scoring model (energy potential, tariff classification) that no off-the-shelf CRM provides — and the custom build costs less than annual CRM licenses for 8+ seats.
- **Supabase real-time for collaborative Kanban** — Leveraged Supabase's real-time subscriptions to keep the Kanban board synchronized across multiple salespeople without polling, ensuring that stage changes and lead assignments are visible instantly to the entire team.
- **Recharts for sales analytics** — Chose Recharts for the leaderboard and conversion rate visualizations, prioritizing React integration simplicity over D3.js flexibility — the right trade-off for standard bar/line/pie charts in an internal sales tool.
- **shadcn/ui for rapid UI development** — Used shadcn/ui components (dialogs, dropdowns, cards, tables) to build a production-quality CRM interface in weeks rather than months, leveraging Tailwind CSS v4 for consistent styling without a custom design system.

## Business Impact

- **Proved domain-specific CRM as a consulting deliverable** — Demonstrated that industry-specific CRMs with integrated scoring models command R$ 25k-60k per engagement, with higher client retention than generic CRM implementations because the scoring logic creates switching costs.
- **Validated Google Places as a scalable lead source** — Showed that Google Places API can systematically generate qualified B2B leads for any industry where commercial establishments are the target customer — applicable to food service, healthcare, retail, and facility management beyond solar energy.
- **Established the "CRM + scoring" pattern** — The architecture of visual pipeline + domain-specific lead scoring + team management is directly portable to insurance broker CRM (policy scoring), mining equipment sales CRM (project scoring), and auction bidder management CRM (bid history scoring).
- **Delivered production tool for active solar sales team** — The CRM serves 8+ salespeople daily at kiiry-crm.vercel.app, providing real-world validation that the tool handles concurrent multi-user workflows, territory management, and ongoing lead import at production scale.
