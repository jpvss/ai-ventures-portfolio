# AI-native agency startup: the complete knowledge base

**An AI-native data infrastructure agency can achieve software-like margins (65–80%) with a 3-person team by using AI as the core delivery engine, not a supplement.** This is exactly what Y Combinator's Aaron Epstein is asking for in the Spring 2026 RFS on AI-Native Agencies. The opportunity sits at the intersection of a $700B+ professional services market ripe for disruption and Brazil's underserved mid-market, where data infrastructure modernization demand far outpaces supply. This document covers everything needed to build, scale, and fund this company — from Claude Code project architecture to YC application strategy to technical stack decisions — serving as the foundational reference for all strategic and architectural decisions.

---

## 1. The YC AI-native agency thesis and why it matters now

### Aaron Epstein's RFS — the mandate

Aaron Epstein, YC Group Partner and co-founder of Creative Market (YC W10, acquired by Autodesk), authored the AI-Native Agencies Request for Startups. His exact words:

> "Agencies have always been crazy hard to scale. Low margins, slow manual work, and the only way to grow is to add more people. But AI changes this. Now instead of selling software to customers to help them do the work, you can charge way more by using the software yourself and selling them the finished product at 100x the price... **That's why agencies of the future will look more like software companies, with software margins.** And they'll scale far bigger than any agencies that exist in these fragmented markets today."

This represents a historic departure from 20 years of VC orthodoxy that services businesses are "uninvestable." Epstein has read **8,000+ YC applications** and champions **revenue per employee** as the defining KPI for modern startups. His thesis: AI breaks the linear relationship between headcount and revenue. A 3-person team generating the output of a 30-person agency IS the thesis.

### YC-funded AI agencies that prove the model

**Manicule (YC X26)** delivers end-to-end technical documentation for developer tool companies. Founded by an 18-year-old who started freelancing for dev tools 3 years prior, the company hit **$15K MRR and profitability** with a team of 5. AI agents handle mechanical work (code verification, auditing, link checking, drafting from OpenAPI specs) while humans refine strategy and quality. One client saw a **30% improvement in answer success rate** with docs shipped in 23 days.

**Perfectly (YC W26)** is an AI-native recruiting agency delivering **4× faster hiring, 10× candidate volume, and 2× higher interview pass rates**. Founded by ex-ML scientists from TikTok and Meta, they reduced recruiting effort from 20 hours to 1 hour per role. Pricing at **15–25% of placement fees** undercuts traditional agencies by ~50%. One client fired all other recruiting agencies two weeks after starting with Perfectly.

**Saudara AI** connects American brands with Indonesian suppliers using an AI agent for factory finding, vetting, sampling, and delivery. Their **12% fee vs. 30–40% for traditional agents** demonstrates how AI-native agencies can structurally undercut incumbents while maintaining quality through human-in-the-loop oversight.

The pattern across all successful YC AI agencies: **deep domain expertise + AI leverage** (not just AI wrappers), demonstrable traction at application time, productized service models with clear scope and fixed pricing, and the "humans for judgment, AI for scale" operating principle.

### The economics that make this work

| Metric | Traditional Agency | AI-Native Agency Target | SaaS Benchmark |
|--------|-------------------|------------------------|----------------|
| Gross margin | 20–35% | **65–80%** | 70–90% |
| Revenue per employee | $172K–$300K | **$500K–$1.2M** | $200K–$610K |
| Scaling model | Linear with headcount | Non-linear, AI-powered | Near-zero marginal cost |
| Delivery speed | Weeks to months | **Days to weeks** | Self-service |

AI-native agencies achieve these margins through four structural advantages: API economics (tasks requiring a $50K/year employee cost $200–500/month in API calls), a **leverage ratio** where AI handles 60–70% of production work, productized delivery with predictable costs, and value-based pricing that decouples revenue from hours worked.

Revenue per employee benchmarks for AI-native companies (2025–2026 data): **Midjourney at $12.5M** (40–50 employees, $500M ARR), **Cursor at $10M+** (50 employees, $500M+ ARR), **FAL at $2.3M+** ($50M+ ARR, 22 people). The average across 35 lean AI-native companies is **$1.2M RPE** (excluding outliers), with 74% being profitable. AI companies grow 4× faster than SaaS with **7–8× fewer employees per dollar of revenue**.

---

## 2. Claude Code project architecture and best practices

### CLAUDE.md — the single highest-leverage file

CLAUDE.md loads into every Claude Code session. Research shows frontier LLMs can follow ~150–200 instructions with reasonable consistency, and Claude Code's system prompt already consumes ~50 instructions. That leaves **~100–150 for your CLAUDE.md**. As instruction count increases, instruction-following degrades uniformly — not just trailing instructions. LLMs bias toward instructions at the peripheries of the prompt (beginning and end).

**What to include vs. exclude:**

| ✅ Include | ❌ Exclude |
|---|---|
| Bash commands Claude can't guess | Anything Claude can figure out by reading code |
| Code style rules that differ from defaults | Standard language conventions Claude already knows |
| Testing instructions and preferred test runners | Detailed API documentation (link to docs instead) |
| Repository etiquette (branch naming, PR conventions) | Information that changes frequently |
| Architectural decisions specific to the project | Long explanations or tutorials |
| Developer environment quirks (required env vars) | File-by-file descriptions of the codebase |
| Common gotchas or non-obvious behaviors | Self-evident practices like "write clean code" |

**Critical rule: "Never send an LLM to do a linter's job."** Use hooks with deterministic formatters (Prettier, Biome) instead of putting code style rules in CLAUDE.md. Keep the file under **200 lines** — HumanLayer's own production CLAUDE.md is under 60 lines. Avoid `/init` — auto-generated files are typically bloated.

### Recommended CLAUDE.md template for this startup

```markdown
# DataCo — AI-Native Data Infrastructure Agency

AI-native agency delivering data infrastructure and automation to mid-market companies.
Monorepo: Next.js 15 frontend, FastAPI backend, shared packages, Claude Sonnet 4.6 primary LLM.

## Architecture
- `/apps/web`: Next.js 15 App Router — client portal, dashboards, diagnostics
- `/apps/api`: FastAPI Python backend — AI agent services, data processing
- `/apps/admin`: Internal ops dashboard
- `/packages/shared`: Shared TypeScript types and utilities
- `/packages/db`: Supabase schema, migrations, RLS policies
- `/packages/agents`: LLM agent definitions, prompts, evaluation rubrics

## Commands
- `pnpm dev`: Start all services (Turborepo)
- `pnpm test`: Run Vitest (prefer single test files)
- `pnpm test:e2e`: Playwright end-to-end tests
- `cd apps/api && uv run pytest`: Python backend tests
- `pnpm db:migrate`: Run Supabase migrations
- `pnpm lint`: Biome check

## Code Style
- TypeScript strict mode, no `any` types
- Named exports only, ES modules
- Python: type hints required, Pydantic for all models
- All LLM calls go through `/packages/agents` — never call Claude API directly from route handlers

## Workflow
- ALWAYS run typecheck after a series of code changes
- Prefer running single tests, not the whole suite
- NEVER commit .env files or API keys
- Feature branches off `main`, squash merge PRs
- Every LLM call MUST be logged to Langfuse

## Important Notes
- Client data isolation: Supabase RLS enforces tenant separation — NEVER bypass
- LGPD compliance: All PII must be anonymized before logging
- See @docs/architecture.md for system design
- See @docs/agent-patterns.md for LLM agent conventions
- See @docs/lgpd-compliance.md for data privacy requirements

## When Compacting
Preserve: modified files list, current test status, active feature branch, pending tasks.
```

### The .claude/ directory structure for this project

```
project-root/
├── CLAUDE.md                          # Team instructions (git-committed)
├── CLAUDE.local.md                    # Personal overrides (gitignored)
├── .mcp.json                          # MCP server configs (git-committed)
├── .claude/
│   ├── settings.json                  # Permissions, hooks (git-committed)
│   ├── settings.local.json            # Personal permissions (gitignored)
│   ├── commands/
│   │   ├── diagnostic-run.md          # /project:diagnostic-run
│   │   ├── deploy.md                  # /project:deploy
│   │   └── client-report.md           # /project:client-report
│   ├── rules/
│   │   ├── code-style.md
│   │   ├── testing.md
│   │   ├── api-conventions.md
│   │   └── lgpd-compliance.md
│   ├── skills/
│   │   ├── data-diagnostic/SKILL.md   # Client data assessment workflow
│   │   ├── report-generation/SKILL.md # PDF/dashboard report creation
│   │   ├── fix-issue/SKILL.md         # GitHub issue resolution
│   │   └── deploy/SKILL.md            # Deployment procedures
│   └── agents/
│       ├── code-reviewer.md           # Security + quality review
│       ├── data-analyst.md            # Data profiling and analysis
│       └── report-writer.md           # Client deliverable generation
├── apps/
│   ├── web/CLAUDE.md                  # Frontend-specific context
│   ├── api/CLAUDE.md                  # Backend-specific context
│   └── admin/CLAUDE.md                # Internal tools context
└── packages/
    ├── agents/CLAUDE.md               # Agent development conventions
    └── db/CLAUDE.md                   # Database conventions
```

### Essential hooks configuration (settings.json)

```json
{
  "permissions": {
    "allow": [
      "Bash(pnpm *)", "Bash(npx *)", "Bash(git *)",
      "Bash(uv run *)", "Bash(cd apps/api && *)", "Read(*)"
    ],
    "deny": [
      "Bash(rm -rf *)", "Read(.env)", "Read(.env.*)",
      "Read(~/.ssh/**)", "Bash(curl * | bash)", "Bash(sudo *)"
    ]
  },
  "hooks": {
    "PostToolUse": [{
      "matcher": "Edit|Write",
      "hooks": [{
        "type": "command",
        "command": "cd $CWD && npx @biomejs/biome format --write $FILEPATH"
      }]
    }]
  }
}
```

Hooks are **deterministic** (100% execution) vs. CLAUDE.md which is advisory (~80%). Use hooks for anything that must happen every time — formatting, linting, test execution.

### Core workflow patterns

**The fundamental loop: Explore → Plan → Implement → Commit**

1. **Explore** (Plan Mode): `read /packages/agents and understand how we define diagnostic workflows`
2. **Plan** (Plan Mode, Ctrl+G to edit): `I want to add a new data quality scoring module. What files need to change?`
3. **Implement** (Normal Mode): `implement the scoring module from your plan. write tests, run the suite, fix failures.`
4. **Commit**: `commit with a descriptive message`

**Context management is the #1 constraint.** Use `/clear` between unrelated tasks. Run `/compact` manually at ~50% context usage. Use subagents for research tasks (they run in separate context windows). If you've corrected Claude 2+ times on the same issue, start a fresh session with a better prompt.

**Subagents for context preservation:**
```
Use subagents to investigate how our Supabase RLS policies handle
multi-tenant data isolation, and whether we have existing utility
functions for client data anonymization.
```

**MCP server configuration (.mcp.json):**
```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": { "GITHUB_PERSONAL_ACCESS_TOKEN": "$GITHUB_TOKEN" }
    },
    "supabase": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres"],
      "env": { "POSTGRES_CONNECTION_STRING": "$DATABASE_URL" }
    },
    "playwright": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-playwright"]
    }
  }
}
```

Each MCP server adds tools to Claude's context. Use MCP Tool Search (v2.1.7+) which dynamically loads tools when they exceed 10% of context window — reducing context usage by up to 95%.

---

## 3. GenAI-first system architecture

### The architectural paradigm shift

The question is no longer "Where do we add AI?" but "Which layer of our system IS the AI?" Every workflow starts with "what can the agent do?" — AI is the core worker, not a supplement. The recommended architecture uses an **Agentic Tier** running alongside traditional application layers.

```
┌─────────────────────────────────────────────────┐
│           Client Interface Layer                 │
│  Natural language intake, dashboards, portal     │
├─────────────────────────────────────────────────┤
│        Orchestration / Router Layer              │
│  LangGraph workflow engine, task routing         │
├─────────────────────────────────────────────────┤
│         Specialized Agent Layer                  │
│  Researcher │ Analyst │ Writer │ QA │ Ops        │
├─────────────────────────────────────────────────┤
│           Memory & Context Layer                 │
│  pgvector + Knowledge Graph │ Working + Long-term│
├─────────────────────────────────────────────────┤
│            Tool & Integration Layer              │
│  APIs, databases, file systems, MCP servers      │
├─────────────────────────────────────────────────┤
│         Evaluation & Guardrails Layer            │
│  LLM-as-Judge, HITL checkpoints, Langfuse        │
├─────────────────────────────────────────────────┤
│          Model Tier (cost-optimized)             │
│  Haiku: routing │ Sonnet: production │ Opus: deep│
└─────────────────────────────────────────────────┘
```

**Model tiering is essential for cost control**: Haiku 4.5 ($1/$5 per MTok) handles classification, extraction, and routing. Sonnet 4.6 ($3/$15 per MTok) covers 80% of production work. Opus 4.6 ($5/$25 per MTok) reserved for complex reasoning tasks only.

### LLM-powered diagnostic pipeline

The diagnostic/audit tool is the core paid product — the entry point that demonstrates capability and converts to larger engagements. Architecture:

```
Client Data Sources → Data Connector (APIs/Files/DB access)
    ↓
Data Profiling Agent (statistical summary, quality metrics, schema analysis)
    ↓
Analysis Agent (pattern detection, anomaly identification, gap analysis)
    ↓
Insight Synthesis Agent (cross-referencing with benchmarks, theme extraction)
    ↓
Report Generation Agent (templated output, visualizations, recommendations)
    ↓
Human Review Checkpoint (founder reviews, adjusts, approves)
    ↓
Client-Ready Deliverable (PDF report + dashboard)
```

Build reusable "audit playbooks" as parameterized agent workflows. Use RAG over past audit results for industry benchmarking. Key profiling tools: YData-Profiling, Great Expectations, DataOps TestGen (the only open-source solution that converts profiling insights into actionable quality checks).

### AI-powered delivery pipeline

The full agency pipeline from intake to monitoring:

```
INTAKE               ANALYSIS             RECOMMENDATIONS
• NL intake form     • Data profiling     • Strategy generation
• Auto-scope         • Gap analysis       • Prioritized actions
• ICP matching       • Benchmark          • ROI estimates
  [HITL Gate 1]       [HITL Gate 2]        [HITL Gate 3]

IMPLEMENTATION       DELIVERY             MONITORING
• Config changes     • Client reporting   • Performance tracking
• Asset generation   • QA review          • Alert agents
• Pipeline builds    • Handoff docs       • Continuous iteration
```

**Design principle**: Use deterministic pipeline steps where possible, with agentic steps for reasoning-heavy tasks. Structured AI workflows still dominate production over fully autonomous agents because they offer reproducibility, governance, and debugging.

### Three-tier quality assurance framework

When AI does the heavy lifting, QA becomes the critical differentiator:

**Tier 1 — Automated screening** (handles 80–90% of cases): LLM-as-Judge evaluates outputs against rubrics for accuracy, relevance, coherence, and task completion. Tools: DeepEval (14+ prebuilt metrics), Opik (open-source).

**Tier 2 — Human review**: Domain experts assess flagged outputs and random 10% sample. Provides ground truth labels that calibrate automated evaluators. Active learning routes low-confidence outputs to humans.

**Tier 3 — Expert validation**: Second-level review for high-stakes deliverables (strategy recommendations, client-facing reports). Resolves disagreements between automated and Tier 2 assessments.

```
Agent Output → LLM-as-Judge Evaluator
    ├── PASS (>threshold) → Random sample 10% for human QA
    ├── UNCERTAIN → Route to domain expert review
    └── FAIL → Return to agent with feedback for revision
    
Human feedback → Update rubrics → Retrain LLM-as-Judge
```

### Data moat architecture — the knowledge core

Every engagement must enrich a **three-layer knowledge system**:

**Knowledge Graph (Neo4j or Memgraph)**: Client entities and relationships, industry patterns and benchmarks, solution templates and outcomes, expert decision trees. Use GraphRAG (Microsoft's approach) for cross-document synthesis — "What are the top patterns across all our retail clients?" is impossible with basic RAG but trivial with knowledge graphs.

**Vector Store (pgvector → Pinecone at scale)**: Past deliverables embedded for semantic search, meeting transcripts, client communications, research artifacts. Enables RAG-powered retrieval of relevant past work when building new deliverables.

**Structured Data Store (Supabase/PostgreSQL)**: Engagement metrics and outcomes, pricing and scoping historical data, quality scores per deliverable, client feedback and NPS. This feeds the benchmarking engine that makes each diagnostic more valuable.

**The flywheel**: each client engagement generates proprietary data (industry benchmarks, common problems, effective solutions) → aggregate data improves assessment tool accuracy → better tool attracts more clients → more data → better tool. This creates a defensible moat competitors can't replicate without doing the same work over years.

**Important caveat**: Pure data moats are eroding as foundation models improve. The real moat is **process moat** — embedding AI directly into workflows so proprietary data becomes an operating advantage. Focus on dynamic, interactive, closed-loop data rather than raw document hoarding.

---

## 4. Every business process flow, systematized

### Lead generation and qualification

**ICP Definition** → Define based on closed-won analysis: company size (50–500 employees), industry vertical, data maturity signals, budget range ($10K–$200K). **Targeted List Building** → Use Clay or Apollo for enriched leads with 85+ data points. **Multi-Channel Outreach** → AI-drafted personalized emails + LinkedIn. **AI Qualification** → Deploy AI qualification agents covering company size, current data stack, use case, timeline, budget. **Lead Scoring** → Predictive scoring on engagement + firmographic fit. **Human Handoff** → Qualified leads routed to commercial cofounder for discovery. **Pipeline Tracking** → HubSpot CRM with automated stage updates.

AI handles: list building, email personalization, initial qualification, scoring, follow-up sequences. Humans handle: ICP definition review (monthly), discovery calls, deal negotiation.

### Sales and proposal generation

**Discovery Call** (30–60 min, AI transcription via Otter.ai) → **Automated Scoping** (AI extracts requirements from transcript) → **Proposal Generation** (templated system with AI-drafted content blocks) → **Pricing Decision** → **Internal Review** (founder reviews in 15 min vs. 2+ hours manual) → **Client Presentation** → **E-signature + Payment** (DocuSign + Stripe).

**Tiered pricing framework:**
- Diagnostic/Audit (Entry): **$5K–$15K** — Data maturity assessment, quick wins ID
- Implementation (Mid): **$25K–$75K** — Data infrastructure build, automation deployment
- Transformation (Enterprise): **$75K–$200K+** — Full data stack transformation

Price on value created, not time spent. If automation saves a client $500K/year, charging $100K (20% of value) delivers a 5× ROI. This is the fundamental unlock — AI breaks the link between time invested and value delivered.

### Client onboarding (the 14-day sprint)

Agencies with structured onboarding retain **32% more clients**. 47% of clients leave within 90 days due to chaotic onboarding. The flow:

**Day 0**: Contract signed → auto-trigger welcome sequence. **Day 1**: Welcome email with team intro, timeline, portal access. **Days 1–3**: Structured intake form (business objectives, KPIs, current data stack, access credentials, stakeholder map). **Days 3–5**: Internal sales-to-delivery handoff (60% of onboarding problems start here). **Days 5–7**: Secure credential collection, kickoff call, workspace setup. **Days 7–14**: Initial data discovery, environment setup. **Day 14**: Onboarding completion check. **Days 30/60/90**: Structured reviews.

### Diagnostic/audit delivery (the core paid product)

**Phase 1 — Business Alignment (Week 1)**: Map 3–5 strategic objectives data should enable. Anchor every finding to a named business priority.

**Phase 2 — Evidence-Based Discovery (Weeks 1–2)**: 12–20 stakeholder interviews. Review existing documentation. Catalog active data products. Rule: **no finding without evidence, no score without proof**.

**Phase 3 — Maturity Scoring (Weeks 2–3)**: Score 6 capability dimensions on 1–5 scale: Data Strategy, Data Governance, Data Quality, Data Infrastructure, Analytics & AI Readiness, Data Culture.

**Phase 4 — Gap Analysis & Roadmap (Week 3)**: Quick wins (30-day), medium-term (90-day), strategic (6–12 month). Interactive PDF with radar chart, dimension scores, prioritized recommendations.

**Phase 5 — Presentation & Action Plan (Weeks 3–4)**: Executive presentation, locked 90-day implementation plan, defined ownership and success metrics.

**Productization opportunity**: Package as a fixed-price **"$10K Data Maturity Assessment"** — the gateway offer that leads to $25K–$200K implementation projects.

### Knowledge management — the 3-person team's force multiplier

Every engagement must produce a reusable artifact. The team's collective intelligence is the competitive moat.

**Codification strategy**: Engagement templates library (by industry, project type), solution patterns repository, client outcome database (anonymized), SOP library. **Personalization strategy**: Post-engagement retrospectives within 48 hours, lessons-learned database with searchable tags, weekly 30-min knowledge-sharing sessions. **AI-enhanced**: RAG-based internal knowledge assistant, automated tagging and categorization, AI-generated engagement summaries, pattern detection across engagements.

### Platform development feedback loop

**Phase 1 — Pattern Recognition (Months 1–12)**: Track recurring client problems. Identify solutions delivered 3+ times with minimal variation. Document the most repeatable, systematizable solutions.

**Phase 2 — Internal Tooling (Months 6–18)**: Build tools to accelerate delivery (data quality profiler, assessment generator, pipeline templates). Measure time savings per engagement. These internal tools become proto-products.

**Phase 3 — Productization (Months 12–24)**: Package internal tool as client-facing product. Start with "service-enabled product" (software + human support). Example: Data Maturity Assessment → self-service assessment tool with consulting interpretation layer.

**Phase 4 — Platform (Months 18–36)**: Decouple product from consulting. Build self-service capabilities. Target revenue split: 30% services / 70% product.

---

## 5. Scaling from three people to $100B without losing your mind

### The AI-leverage pyramid

**Level 1 — Automate administrative (save 40+ hrs/week)**: Lead routing, CRM updates, scheduling, invoicing, reporting. Each automation saves 15–30 min; across 100 leads + 50 accounts = 40+ hours recaptured weekly.

**Level 2 — AI-assisted delivery (3–5× throughput)**: AI drafts proposals (15 min vs. 2 hours), generates initial assessment reports, writes documentation, monitors pipelines 24/7. Early adopters report automating **70–80% of operations**, recovering 9–10 work hours per client per week.

**Level 3 — Productized services (decouple revenue from time)**: Fixed-price packages with standardized delivery. One person with AI delivers what previously required 5–10.

**Level 4 — Platform revenue (true scale)**: Self-service tools built from consulting patterns. Revenue not tied to human hours.

### The 3-person team structure

- **Founder/Technical Lead**: Architecture, implementation, AI-assisted coding, senior delivery oversight
- **Commercial Cofounder**: Sales, client relationships, strategy, proposal review
- **SME Partner**: Domain expertise, QA, client advisory, knowledge management
- **AI Agents**: Lead qualification, proposal drafting, data profiling, report generation, monitoring, documentation, invoicing

**Target revenue trajectory**: Year 1: $500K ($167K RPE). Year 2: $1M ($333K RPE). Year 3: $2–3M with 5–8 people ($375K–$600K RPE, approaching AI-native benchmarks).

### Brazil to US expansion playbook

**Phase 1 — Establish US credibility (Months 1–6)**: Register Delaware C-Corp (YC requires US, Canada, Cayman, or Singapore incorporation). US bank account and Stripe for payment processing. Build English-language case studies and content. Leverage timezone advantage — Brazil (BRT) overlaps with US Eastern business hours.

**Phase 2 — Bridge strategy (Months 3–12)**: Target Brazilian companies with US operations (natural bridge clients) and US companies with Brazil/LatAm operations. Position the cost advantage: LatAm operating costs 30–50% lower than US equivalents.

**Phase 3 — Direct US sales (Months 6–18)**: AI-powered outbound to US mid-market. Content marketing targeting data infrastructure pain points. Partner with US-based complementary consultancies.

**The structural advantage**: A team billing at US market rates ($150–300/hr equivalent) while operating from Brazil achieves **70–80% gross margins** without extraordinary efficiency. Adding AI leverage on top creates margins that look more like SaaS than services.

### Vertical strategy — go deep first

**Year 1**: Pick ONE industry vertical in Brazil (retail/e-commerce, financial services, or agribusiness). Become the known expert. Build reusable templates, benchmarks, and case studies. Specialist agencies charge **2–3× what generalists charge**.

**Year 2**: Leverage patterns to adjacent vertical. 60–70% of solutions transfer; customize 30–40%.

**Year 3+**: Core platform serves multiple verticals with vertical-specific modules on top.

**Key principle**: "You can't scale what you can't repeat." Vertical focus enables repeatability.

### Pricing evolution as you scale

**Stage 1 — Project-based** (now): Diagnostic $5K–$15K, Implementation $25K–$75K. Efficiency gains increase your effective hourly rate.

**Stage 2 — Value-based** (growth): Price on client ROI. If automation saves $500K/year, charge $100K.

**Stage 3 — Retainer + usage hybrid** (scale): Monthly retainer $5K–$25K/mo plus usage-based platform features.

**Stage 4 — SaaS subscription** (platform): Self-service tiers with published pricing. Services become premium add-on.

---

## 6. YC Summer 2026 application — the strategic playbook

### The critical details

**Application deadline**: May 4, 2026 at 8pm PT. Decision notification by June 5. Batch runs July–September in San Francisco (in-person attendance required). **Deal**: $500K total — $125K for 7% equity (post-money SAFE) + $375K on uncapped SAFE with MFN provision. Acceptance rate: under 1% (W24: 260 companies from 27,000+ applications). Recent batches: **85–90% AI-focused**, ~80–85% B2B/enterprise.

### Why this company is perfectly positioned

The startup is building exactly what Aaron Epstein's RFS explicitly requests. Three alignment points to hammer in the application:

1. **Perfect RFS match**: Aaron Epstein literally wrote an RFS entry asking for this type of company — an agency achieving software margins through AI
2. **Brazil as strategic beachhead**: Massive underserved market, structural cost advantages, proven model ready for US expansion
3. **Revenue per employee embodiment**: 3-person team with software margins is the thesis Aaron Epstein champions on X/Twitter

### What YC expects from agency applicants

From YC's FAQ: "On average, 40% of the companies we fund in each batch are just an idea." Basedash was accepted with **$30/month revenue**. The key is "progress-for-your-stage" — if pre-launch, they want a great team and unique insight. If you've been working for a year, they expect traction.

**For an AI agency, strong metrics include**: number of clients served, revenue (even small amounts), gross margins approaching software levels, delivery speed vs. traditional (e.g., "2 weeks vs. 3 months"), revenue per employee, and week-over-week growth rate. YC W25 batch companies in aggregate grew **10% per week**.

### The Brazil/LatAm challenge

YC's W24 batch had only **one** Latin American startup, down from 33 in W22. Key factors: return to in-person SF batches, AI focus shifting advantage to US-based founders, and reduced global outreach.

**How to overcome this**: Frame Brazil as beachhead with US as target market — "We started in Brazil where demand is enormous and competition is low. We've proven the model. Now we're expanding to the US where TAM is 10× larger." Show global ambition — don't be "data infrastructure for Brazil," be **"AI-native data infrastructure agency, starting in Brazil, scaling globally."** Be ready to commit to SF for the batch. Incorporate (or flip) to a US entity.

### The one-liner (most important application field)

Draft: **"We're an AI-native agency that builds data infrastructure and automation for mid-market companies — delivering in weeks what traditional firms take months, at software-like margins."**

### Preparing for the interview (10 minutes, Zoom)

YC says: "We just want to have a conversation... Founders looking for an edge sometimes think lots of interview preparation will help. We sometimes notice that founders overprepare."

**The Rule of Three** (from Mantys founder, YC W23): Emphasize three core facets — the vast potential of the market, initial traction, and the robust backgrounds of the founders.

**Agency-specific questions to prepare:**
- "How is this different from a consulting firm?" → Software margins, non-linear scaling, data flywheel
- "What happens when you need more people to serve more clients?" → AI handles 70% of delivery; each engagement makes the next faster
- "What's your path to software?" → Internal tools become external products; services are the fastest path to building software people actually want
- "Why won't clients just do this themselves?" → Same reason companies hire accountants — data infrastructure is specialized, they want outcomes not tools
- "What's your gross margin?" → Know this number cold, target 65%+

### Pre-May 4 action items

Apply early — rolling review means earlier is better. Get any revenue or client metrics possible. Prepare a working demo of the diagnostic tool. Record a 1-minute authentic video showing team dynamic. Incorporate in the US (Delaware C-Corp). Reference the RFS explicitly in the application.

---

## 7. Technical stack — specific recommendations with pricing

### Starter stack (Months 1–6, ~$170–360/month)

| Layer | Tool | Monthly Cost |
|-------|------|-------------|
| LLM API | Claude Sonnet 4.6 (primary) + Haiku 4.5 (routing) | $50–200 |
| Dev Tool | Claude Code | Included in plan |
| Frontend | Next.js 15 + TypeScript + Tailwind + Tremor | Free (OSS) |
| Backend | FastAPI (Python) for AI services | Free (OSS) |
| Database | Supabase Pro (São Paulo region) | $25/month |
| Vector DB | pgvector (Supabase extension) | $0 included |
| Auth | Supabase Auth with RLS | $0 included |
| Deployment (FE) | Vercel Pro | $20/user/month |
| Deployment (BE) | Railway | $15–40/month |
| Workflow | n8n (self-hosted on Railway) | $0 |
| LLM Observability | Langfuse (self-hosted) | $0 |
| Analytics | PostHog Cloud free tier | $0 |
| Error Tracking | Sentry free tier | $0 |
| CI/CD | GitHub Actions | $0 |
| PDF Reports | @react-pdf/renderer + Claude | $0 + API costs |
| CRM | HubSpot free tier | $0 |

### Scale stack (Months 6–18, ~$500–2,500/month)

Upgrade path: Supabase Team ($599) or add Neon for branching, Pinecone Serverless for vector search at scale, Inngest for durable TypeScript workflows, Braintrust for LLM evaluation pipelines, Vanta for SOC 2 preparation when pursuing US enterprise clients.

### Claude API production patterns

**Prompt caching** delivers 70–80% cost savings for repetitive workflows. Cached prefixes expire after 5 minutes of inactivity — high-traffic endpoints benefit most. **Batch API** available for Sonnet and Opus with support for up to 300K output tokens; use for non-real-time workloads like report generation and bulk processing. **Structured outputs** (JSON mode) achieve 95%+ consistency. Use **streaming** for all user-facing interactions to reduce perceived latency.

Rate limits start at ~60 RPM and 60K TPM, increasing with usage history. Implement exponential backoff retry logic. Tool use adds latency — each tool call is a separate round-trip, so minimize tool calls by providing sufficient context upfront.

### Agent orchestration recommendation

Start with the **Anthropic Agent SDK** for simple agent loops (native Claude integration, minimal abstraction). Adopt **LangGraph** when multi-agent coordination is needed (graph-based orchestration with cycles, persistence, human-in-the-loop, 8,200+ GitHub stars). Avoid heavy frameworks initially — many production systems use minimal abstractions with raw API calls and only add frameworks when complexity demands it.

### LGPD compliance technical implementation

**Priority 0 (immediate)**: Data encryption at rest (Supabase default AES-256), encryption in transit (TLS 1.3), access control via Supabase RLS + role-based access, audit trail logging, comprehensive Portuguese-language privacy policy.

**Priority 1 (Month 2)**: Consent management tracking in Supabase, data residency in São Paulo region, anonymization/pseudonymization for analytics data.

**Priority 2 (US expansion)**: SOC 2 preparation via Vanta or Drata ($300+/month). Required for US enterprise trust.

**AI-specific privacy**: Never store raw client data in LLM prompts or logs — anonymize before logging. Use Claude API (not claude.ai) — API data is not used for training. Implement data retention policies per client agreement. Fines for LGPD violations: up to 2% of Brazilian revenue (capped at R$50M per infraction). Resolution CD/ANPD No. 2/2022 provides simplified requirements for startups.

### Key architectural principles

**Composable and modular**: Every component replaceable via API. Use Claude today, swap models tomorrow without rewriting business logic. **Instrument everything from day one**: Every LLM call, client interaction, and workflow step is logged and queryable. **PostgreSQL as backbone**: Supabase gives relational data, vector search, auth, real-time, and file storage in one platform. **TypeScript + Python hybrid**: 80% TypeScript (frontend, API, automation) for hiring speed; 20% Python (AI services, data processing) for ML ecosystem. **Self-hostable where possible**: Langfuse, n8n, PostHog can all be self-hosted for LGPD data sovereignty. **Cost-conscious model routing**: Cheapest model that clears the quality bar, optimized with caching and batching.

---

## 8. Multi-agent system design for agency operations

### The six orchestration patterns to deploy

**Coordinator-Worker** (for content pipelines): Central orchestrator delegates to specialist workers — researcher, writer, editor, publisher agents. Use for diagnostic report generation.

**Sequential Pipeline** (for delivery flows): Agents process in order, each building on previous output. Data analysis → insight generation → report writing → QA review.

**Parallel Fan-out/Fan-in** (for multi-source research): Multiple agents work simultaneously across different data types, results merged. Use for client data profiling across databases, APIs, and files.

**Reflection/Self-Critique** (for quality loops): Agent reviews its own work and iterates. Use for improving generated content before human review.

### Structured context passing between agents

Use **typed context objects** with only relevant fields per agent — 200–500 tokens vs. 5,000–20,000 for full conversation forwarding. This is the production-recommended approach from orchestration research.

### Agent communication protocols

**MCP (Model Context Protocol)** for how agents access external tools and data sources. **A2A (Agent-to-Agent Protocol, Google)** for inter-agent communication at scale. Both use JSON-RPC 2.0 and are open standards.

### AI agents for internal operations

**Sales**: AI SDR agents handle lead qualification, multi-channel outreach, CRM hygiene, and meeting booking. Teams report **70% cost reduction** vs. human SDRs.

**Onboarding**: AI creates project workspaces, generates credentials, schedules kickoffs, personalizes materials, monitors progress. Case study: retirement plan administrator reduced onboarding from 5–9 hours to **90 minutes**, saving $1.3M annually.

**Project management**: AI agent tracks status, identifies blockers, communicates via Slack. Saves **15 hours/week** in coordination.

**Invoicing**: AI invoice pipeline handles OCR extraction, validation, categorization, routing, and accounting sync. Agency case study: automated processing of 60 invoices/month from freelancers saved admin lead **6–8 hours/week**.

---

## Conclusion — the strategic synthesis

This startup sits at the exact intersection of what YC is funding, what the market demands, and what AI now makes possible. The core insight is Aaron Epstein's: **sell the finished product, not the tool**. Use AI internally to deliver data infrastructure outcomes at software-like margins, and build every engagement to feed a proprietary data flywheel that makes the next engagement faster and better.

The path from here to YC S26 acceptance requires executing on three fronts simultaneously before May 4: shipping a working diagnostic tool built on the Claude API stack documented here, landing 2–3 paying clients in Brazil to demonstrate the model works, and framing the narrative as "AI-native agency achieving software margins today, building toward a self-serve platform tomorrow." The CLAUDE.md and project architecture laid out in this document should serve as the operational brain of the company — not just a coding reference, but a strategic decision-making framework that enables Claude Code to act as the senior staff product engineer this 3-person team needs.

The companies that win in this space won't be the ones with the most sophisticated AI. They'll be the ones who build the tightest feedback loop between client work and product development, accumulating proprietary data and process advantages that compound over time. Every diagnostic delivered, every pipeline built, every automation deployed should make the system smarter. That's the moat. That's what scales.