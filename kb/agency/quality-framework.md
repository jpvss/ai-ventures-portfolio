---
title: Three-Tier Quality Assurance Framework
type: agency
vertical: cross-vertical
language: en
last_compiled: 2026-04-02
sources:
  - kb/raw/agency-setup.md
freshness: current
tags:
  - quality
  - qa
  - llm-as-judge
  - evaluation
  - knowledge-management
  - data-moat
---

# Three-Tier Quality Assurance Framework

When AI does the heavy lifting, QA becomes the critical differentiator.

---

## Tier 1 — Automated Screening (80-90% of Cases)

LLM-as-Judge evaluates outputs against rubrics for:
- **Accuracy**: Factual correctness, data integrity
- **Relevance**: Alignment with client objectives and scope
- **Coherence**: Logical flow, internal consistency
- **Task completion**: All requirements addressed

### Tools
- **DeepEval**: 14+ prebuilt metrics for LLM evaluation
- **Opik**: Open-source evaluation framework

### Flow
```
Agent Output → LLM-as-Judge Evaluator
    ├── PASS (>threshold) → Random sample 10% for human QA
    ├── UNCERTAIN → Route to domain expert review
    └── FAIL → Return to agent with feedback for revision

Human feedback → Update rubrics → Retrain LLM-as-Judge
```

---

## Tier 2 — Human Review

- Domain experts assess flagged outputs from Tier 1
- Random 10% sample of PASS outputs reviewed for calibration
- Provides ground truth labels that calibrate automated evaluators
- Active learning routes low-confidence outputs to humans
- Focus areas: nuanced domain accuracy, client-specific context, strategic recommendations

---

## Tier 3 — Expert Validation

- Second-level review for high-stakes deliverables
- Applied to: strategy recommendations, client-facing reports, executive presentations
- Resolves disagreements between automated and Tier 2 assessments
- Final quality gate before client delivery

---

## Quality Metrics

| Metric | Target | Measurement |
|--------|--------|-------------|
| Automated pass rate | 80-90% | Tier 1 PASS / total outputs |
| Human override rate | <10% | Tier 2 corrections / Tier 1 PASS |
| Client satisfaction | >4.5/5 | Post-engagement survey |
| Revision requests | <15% | Client-requested changes / deliverables |
| Time to delivery | 2-4 weeks | Diagnostic completion time |

---

## Knowledge Management Architecture

Every engagement must enrich a **three-layer knowledge system** that creates a defensible data moat.

### Layer 1 — Knowledge Graph (Neo4j or Memgraph)
- Client entities and relationships
- Industry patterns and benchmarks
- Solution templates and outcomes
- Expert decision trees
- Use **GraphRAG** (Microsoft's approach) for cross-document synthesis
- Example query: "What are the top patterns across all our retail clients?" — impossible with basic RAG, trivial with knowledge graphs

### Layer 2 — Vector Store (pgvector → Pinecone at Scale)
- Past deliverables embedded for semantic search
- Meeting transcripts
- Client communications
- Research artifacts
- Enables RAG-powered retrieval of relevant past work when building new deliverables

### Layer 3 — Structured Data Store (Supabase/PostgreSQL)
- Engagement metrics and outcomes
- Pricing and scoping historical data
- Quality scores per deliverable
- Client feedback and NPS
- Feeds the benchmarking engine that makes each diagnostic more valuable

---

## The Flywheel: Each Engagement Generates Proprietary Data

```
Client Engagement
    ↓
Proprietary Data Generated
  (industry benchmarks, common problems, effective solutions)
    ↓
Aggregate Data Improves Assessment Tool Accuracy
    ↓
Better Tool Attracts More Clients
    ↓
More Data → Better Tool → More Clients
    ↓
Defensible Moat (competitors can't replicate without years of work)
```

### Important Caveat on Data Moats
Pure data moats are eroding as foundation models improve. The real moat is **process moat** — embedding AI directly into workflows so proprietary data becomes an operating advantage. Focus on dynamic, interactive, closed-loop data rather than raw document hoarding.

### What Makes the Moat Real
The companies that win won't be the ones with the most sophisticated AI. They'll be the ones who build the tightest feedback loop between client work and product development, accumulating proprietary data and process advantages that compound over time. Every diagnostic delivered, every pipeline built, every automation deployed should make the system smarter.
