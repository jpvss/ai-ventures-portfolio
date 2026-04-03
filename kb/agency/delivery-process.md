---
title: Engagement Delivery Process
type: agency
vertical: cross-vertical
language: en
last_compiled: 2026-04-02
sources:
  - kb/raw/agency-setup.md
freshness: current
tags:
  - delivery
  - process
  - onboarding
  - diagnostic
  - operations
  - knowledge-management
---

# Engagement Delivery Process

## Core Workflow: Explore, Plan, Implement, Commit

1. **Explore**: Understand the client's current state — data stack, pain points, business objectives
2. **Plan**: Scope the engagement, define deliverables, set milestones
3. **Implement**: Execute with AI-powered delivery pipeline
4. **Commit**: Deliver, review, hand off, capture learnings

---

## LLM-Powered Diagnostic Pipeline (5 Agents)

The diagnostic/audit tool is the core paid product — the entry point that demonstrates capability and converts to larger engagements.

```
Client Data Sources → Data Connector (APIs/Files/DB access)
    ↓
Agent 1: Data Profiling Agent
  (statistical summary, quality metrics, schema analysis)
    ↓
Agent 2: Analysis Agent
  (pattern detection, anomaly identification, gap analysis)
    ↓
Agent 3: Insight Synthesis Agent
  (cross-referencing with benchmarks, theme extraction)
    ↓
Agent 4: Report Generation Agent
  (templated output, visualizations, recommendations)
    ↓
Agent 5: Human Review Checkpoint
  (founder reviews, adjusts, approves)
    ↓
Client-Ready Deliverable (PDF report + dashboard)
```

### Key Profiling Tools
- YData-Profiling
- Great Expectations
- DataOps TestGen (only open-source solution that converts profiling insights into actionable quality checks)

### Design Principle
Use deterministic pipeline steps where possible, with agentic steps for reasoning-heavy tasks. Structured AI workflows dominate production over fully autonomous agents because they offer reproducibility, governance, and debugging.

---

## 14-Day Client Onboarding Sprint

Agencies with structured onboarding retain **32% more clients**. 47% of clients leave within 90 days due to chaotic onboarding.

| Day | Activity |
|-----|----------|
| **Day 0** | Contract signed → auto-trigger welcome sequence |
| **Day 1** | Welcome email with team intro, timeline, portal access |
| **Days 1-3** | Structured intake form: business objectives, KPIs, current data stack, access credentials, stakeholder map |
| **Days 3-5** | Internal sales-to-delivery handoff (60% of onboarding problems start here) |
| **Days 5-7** | Secure credential collection, kickoff call, workspace setup |
| **Days 7-14** | Initial data discovery, environment setup |
| **Day 14** | Onboarding completion check |
| **Day 30** | First structured review |
| **Day 60** | Second structured review |
| **Day 90** | Third structured review — retention critical checkpoint |

---

## 4-Phase Diagnostic Delivery

### Phase 1 — Business Alignment (Week 1)
- Map 3-5 strategic objectives data should enable
- Anchor every finding to a named business priority
- Establish success metrics upfront

### Phase 2 — Evidence-Based Discovery (Weeks 1-2)
- 12-20 stakeholder interviews
- Review existing documentation
- Catalog active data products
- Rule: **no finding without evidence, no score without proof**

### Phase 3 — Maturity Scoring (Weeks 2-3)
Score 6 capability dimensions on 1-5 scale:
1. Data Strategy
2. Data Governance
3. Data Quality
4. Data Infrastructure
5. Analytics & AI Readiness
6. Data Culture

### Phase 4 — Gap Analysis & Roadmap (Week 3)
- Quick wins (30-day)
- Medium-term (90-day)
- Strategic (6-12 month)
- Interactive PDF with radar chart, dimension scores, prioritized recommendations

### Phase 5 — Presentation & Action Plan (Weeks 3-4)
- Executive presentation
- Locked 90-day implementation plan
- Defined ownership and success metrics

---

## Every Business Process Flow

### Lead Generation and Qualification
1. **ICP Definition** → Company size (50-500 employees), industry vertical, data maturity signals, budget range ($10K-$200K)
2. **Targeted List Building** → Clay or Apollo for enriched leads with 85+ data points
3. **Multi-Channel Outreach** → AI-drafted personalized emails + LinkedIn
4. **AI Qualification** → AI agents covering company size, current data stack, use case, timeline, budget
5. **Lead Scoring** → Predictive scoring on engagement + firmographic fit
6. **Human Handoff** → Qualified leads routed to commercial cofounder for discovery
7. **Pipeline Tracking** → HubSpot CRM with automated stage updates

**AI handles**: List building, email personalization, initial qualification, scoring, follow-up sequences.
**Humans handle**: ICP definition review (monthly), discovery calls, deal negotiation.

### Sales and Proposal Generation
1. **Discovery Call** (30-60 min, AI transcription via Otter.ai)
2. **Automated Scoping** (AI extracts requirements from transcript)
3. **Proposal Generation** (templated system with AI-drafted content blocks)
4. **Pricing Decision** (value-based, referencing tier framework)
5. **Internal Review** (founder reviews in 15 min vs. 2+ hours manual)
6. **Client Presentation**
7. **E-signature + Payment** (DocuSign + Stripe)

### Client Onboarding
See [14-Day Client Onboarding Sprint](#14-day-client-onboarding-sprint) above.

### Diagnostic Delivery
See [4-Phase Diagnostic Delivery](#4-phase-diagnostic-delivery) above.

### Knowledge Management
Every engagement must produce a reusable artifact. The team's collective intelligence is the competitive moat.

- **Codification**: Engagement templates library (by industry, project type), solution patterns repository, client outcome database (anonymized), SOP library
- **Personalization**: Post-engagement retrospectives within 48 hours, lessons-learned database with searchable tags, weekly 30-min knowledge-sharing sessions
- **AI-enhanced**: RAG-based internal knowledge assistant, automated tagging and categorization, AI-generated engagement summaries, pattern detection across engagements

---

## Platform Development Feedback Loop

### Phase 1 — Pattern Recognition (Months 1-12)
- Track recurring client problems
- Identify solutions delivered 3+ times with minimal variation
- Document the most repeatable, systematizable solutions

### Phase 2 — Internal Tooling (Months 6-18)
- Build tools to accelerate delivery (data quality profiler, assessment generator, pipeline templates)
- Measure time savings per engagement
- Internal tools become proto-products

### Phase 3 — Productization (Months 12-24)
- Package internal tool as client-facing product
- Start with "service-enabled product" (software + human support)
- Example: Data Maturity Assessment → self-service assessment tool with consulting interpretation layer

### Phase 4 — Platform (Months 18-36)
- Decouple product from consulting
- Build self-service capabilities
- Target revenue split: 30% services / 70% product

---

## AI-Powered Delivery Pipeline (Full Flow)

```
INTAKE               ANALYSIS             RECOMMENDATIONS
- NL intake form     - Data profiling     - Strategy generation
- Auto-scope         - Gap analysis       - Prioritized actions
- ICP matching       - Benchmark          - ROI estimates
  [HITL Gate 1]       [HITL Gate 2]        [HITL Gate 3]

IMPLEMENTATION       DELIVERY             MONITORING
- Config changes     - Client reporting   - Performance tracking
- Asset generation   - QA review          - Alert agents
- Pipeline builds    - Handoff docs       - Continuous iteration
```
