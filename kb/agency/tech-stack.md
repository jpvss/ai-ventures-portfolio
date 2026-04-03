---
title: Technology Stack Decisions and Rationale
type: agency
vertical: cross-vertical
language: en
last_compiled: 2026-04-02
sources:
  - kb/raw/agency-setup.md
freshness: current
tags:
  - tech-stack
  - architecture
  - claude-api
  - lgpd
  - multi-agent
  - infrastructure
---

# Technology Stack Decisions and Rationale

## Starter Stack (Months 1-6, ~$170-360/month)

| Layer | Tool | Monthly Cost |
|-------|------|-------------|
| LLM API | Claude Sonnet 4.6 (primary) + Haiku 4.5 (routing) | $50-200 |
| Dev Tool | Claude Code | Included in plan |
| Frontend | Next.js 15 + TypeScript + Tailwind + Tremor | Free (OSS) |
| Backend | FastAPI (Python) for AI services | Free (OSS) |
| Database | Supabase Pro (Sao Paulo region) | $25/month |
| Vector DB | pgvector (Supabase extension) | $0 included |
| Auth | Supabase Auth with RLS | $0 included |
| Deployment (FE) | Vercel Pro | $20/user/month |
| Deployment (BE) | Railway | $15-40/month |
| Workflow | n8n (self-hosted on Railway) | $0 |
| LLM Observability | Langfuse (self-hosted) | $0 |
| Analytics | PostHog Cloud free tier | $0 |
| Error Tracking | Sentry free tier | $0 |
| CI/CD | GitHub Actions | $0 |
| PDF Reports | @react-pdf/renderer + Claude | $0 + API costs |
| CRM | HubSpot free tier | $0 |

---

## Scale Stack (Months 6-18, ~$500-2,500/month)

| Upgrade | Purpose | Cost |
|---------|---------|------|
| Supabase Team | Higher limits, better support | $599/month |
| Neon | Database branching for development | Variable |
| Pinecone Serverless | Vector search at scale | Variable |
| Inngest | Durable TypeScript workflows | Variable |
| Braintrust | LLM evaluation pipelines | Variable |
| Vanta | SOC 2 preparation for US enterprise clients | $300+/month |

---

## Claude API Production Patterns

### Prompt Caching (70-80% Cost Savings)
- Cache repetitive prefixes (system prompts, few-shot examples, context documents)
- Cached prefixes expire after 5 minutes of inactivity
- High-traffic endpoints benefit most
- Essential for diagnostic pipelines where the same rubrics/templates are used across clients

### Batch API
- Available for Sonnet and Opus
- Supports up to 300K output tokens
- Use for non-real-time workloads: report generation, bulk processing, overnight analytics
- Lower cost than synchronous calls

### Structured Outputs
- JSON mode achieves 95%+ consistency
- Critical for agent pipelines where downstream agents parse upstream output
- Use Pydantic models (Python) or Zod schemas (TypeScript) for validation

### Streaming
- Use for all user-facing interactions
- Reduces perceived latency significantly
- Essential for portal/dashboard experiences

### Rate Limits and Best Practices
- Start at ~60 RPM and 60K TPM, increasing with usage history
- Implement exponential backoff retry logic
- Tool use adds latency — each tool call is a separate round-trip
- Minimize tool calls by providing sufficient context upfront

### Model Tiering (Cost-Optimized)
| Model | Cost (Input/Output per MTok) | Use Case |
|-------|------------------------------|----------|
| Haiku 4.5 | $1/$5 | Classification, extraction, routing |
| Sonnet 4.6 | $3/$15 | 80% of production work |
| Opus 4.6 | $5/$25 | Complex reasoning tasks only |

---

## Agent Orchestration

### Recommended Path
1. **Start**: Anthropic Agent SDK — native Claude integration, minimal abstraction, simple agent loops
2. **Scale to**: LangGraph — when multi-agent coordination is needed (graph-based orchestration with cycles, persistence, human-in-the-loop, 8,200+ GitHub stars)

### Principle
Avoid heavy frameworks initially. Many production systems use minimal abstractions with raw API calls and only add frameworks when complexity demands it.

---

## Multi-Agent System Design

### Six Orchestration Patterns

**1. Coordinator-Worker** (Content Pipelines)
- Central orchestrator delegates to specialist workers
- Researcher, writer, editor, publisher agents
- Use for: diagnostic report generation

**2. Sequential Pipeline** (Delivery Flows)
- Agents process in order, each building on previous output
- Data analysis → insight generation → report writing → QA review

**3. Parallel Fan-out/Fan-in** (Multi-Source Research)
- Multiple agents work simultaneously across different data types
- Results merged at convergence point
- Use for: client data profiling across databases, APIs, and files

**4. Reflection/Self-Critique** (Quality Loops)
- Agent reviews its own work and iterates
- Use for: improving generated content before human review

**5. Structured Context Passing**
- Typed context objects with only relevant fields per agent
- 200-500 tokens vs. 5,000-20,000 for full conversation forwarding
- Production-recommended approach from orchestration research

**6. Agent Communication Protocols**
- **MCP** (Model Context Protocol): How agents access external tools and data sources
- **A2A** (Agent-to-Agent Protocol, Google): Inter-agent communication at scale
- Both use JSON-RPC 2.0, both open standards

---

## Internal Operations Agents

### Sales Agent
- Lead qualification, multi-channel outreach, CRM hygiene, meeting booking
- **70% cost reduction** vs. human SDRs

### Onboarding Agent
- Creates project workspaces, generates credentials, schedules kickoffs
- Personalizes materials, monitors progress
- Case study: retirement plan administrator reduced onboarding from 5-9 hours to **90 minutes**, saving $1.3M annually

### Project Management Agent
- Tracks status, identifies blockers, communicates via Slack
- Saves **15 hours/week** in coordination

### Invoicing Agent
- OCR extraction, validation, categorization, routing, accounting sync
- Case study: automated processing of 60 invoices/month from freelancers saved admin lead **6-8 hours/week**

---

## LGPD Compliance Priorities

### Priority 0 — Immediate
- Data encryption at rest (Supabase default AES-256)
- Encryption in transit (TLS 1.3)
- Access control via Supabase RLS + role-based access
- Audit trail logging
- Comprehensive Portuguese-language privacy policy

### Priority 1 — Month 2
- Consent management tracking in Supabase
- Data residency in Sao Paulo region
- Anonymization/pseudonymization for analytics data

### Priority 2 — US Expansion
- SOC 2 preparation via Vanta or Drata ($300+/month)
- Required for US enterprise trust

### AI-Specific Privacy Requirements
- **Never** store raw client data in LLM prompts or logs — anonymize before logging
- Use Claude API (not claude.ai) — API data is not used for training
- Implement data retention policies per client agreement
- Fines for LGPD violations: up to 2% of Brazilian revenue (capped at R$50M per infraction)
- Resolution CD/ANPD No. 2/2022 provides simplified requirements for startups

---

## GenAI-First 7-Layer Architecture

```
┌─────────────────────────────────────────────────┐
│  Layer 1: Client Interface Layer                │
│  Natural language intake, dashboards, portal    │
├─────────────────────────────────────────────────┤
│  Layer 2: Orchestration / Router Layer          │
│  LangGraph workflow engine, task routing        │
├─────────────────────────────────────────────────┤
│  Layer 3: Specialized Agent Layer               │
│  Researcher | Analyst | Writer | QA | Ops       │
├─────────────────────────────────────────────────┤
│  Layer 4: Memory & Context Layer                │
│  pgvector + Knowledge Graph | Working + Long-   │
│  term memory                                    │
├─────────────────────────────────────────────────┤
│  Layer 5: Tool & Integration Layer              │
│  APIs, databases, file systems, MCP servers     │
├─────────────────────────────────────────────────┤
│  Layer 6: Evaluation & Guardrails Layer         │
│  LLM-as-Judge, HITL checkpoints, Langfuse      │
├─────────────────────────────────────────────────┤
│  Layer 7: Model Tier (cost-optimized)           │
│  Haiku: routing | Sonnet: production | Opus:    │
│  deep reasoning                                 │
└─────────────────────────────────────────────────┘
```

### Key Architectural Principles

1. **Composable and modular**: Every component replaceable via API. Use Claude today, swap models tomorrow without rewriting business logic.
2. **Instrument everything from day one**: Every LLM call, client interaction, and workflow step is logged and queryable.
3. **PostgreSQL as backbone**: Supabase gives relational data, vector search, auth, real-time, and file storage in one platform.
4. **TypeScript + Python hybrid**: 80% TypeScript (frontend, API, automation) for hiring speed; 20% Python (AI services, data processing) for ML ecosystem.
5. **Self-hostable where possible**: Langfuse, n8n, PostHog can all be self-hosted for LGPD data sovereignty.
6. **Cost-conscious model routing**: Cheapest model that clears the quality bar, optimized with caching and batching.
