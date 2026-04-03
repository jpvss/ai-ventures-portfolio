---
title: "LicitaLeads — Architecture"
type: project
slug: licitaleads
language: en
last_compiled: 2026-04-02
---

# LicitaLeads — Technical Architecture

## Tech Stack Choices and Rationale

- **Next.js 16 + React 19:** Server Components for data-heavy dashboard (leads load server-side), Client Components only for interactive filters and table expansions.
- **Static JSON (no database):** Zero-infrastructure MVP — pre-processed data served as static JSON files (~8.2MB display window). Eliminates database costs; data freshness depends on pipeline re-runs.
- **Zod 4:** Runtime validation at API boundaries — ensures PNCP, BrasilAPI, and Minha Receita responses match expected schemas before processing.
- **Resend:** Transactional email for daily lead digest (single hardcoded recipient during MVP).
- **tsx:** TypeScript execution for 9 pipeline scripts without separate build step.
- **Vercel free tier:** Zero-cost deployment with `CLIENT_LEAD_CAP = 2,000` to stay under 50MB serverless function size.

## Data Pipeline Architecture

```
PNCP API (Consulta + Integration)
  ↓
Scripts (run locally, output to data/)
  fetch-contratos.ts       → contratos.json (signed contracts, 30d window)
  fetch-contratacoes.ts    → contratacoes.json (open + recently updated)
  fetch-resultados.ts      → adjudicacoes.json (winners per item)
  enrich-empresas.ts       → empresas.json (CNPJ enrichment)
  check-debarment.ts       → debarment.json (CEIS/CNEP flags)
  fetch-editais.ts         → editais/*.pdf + edital-metadata.json
  extract-editais.ts       → edital-extracts.json (text + keyword filtering)
  analyze-editais.ts       → edital-analysis.json (LLM structured extraction)
  ↓
score.ts (join all sources + composite scoring)
  ↓
data/leads.json + data/garantia-leads.json (denormalized, sorted by score)
  ↓
React Server Components → Next.js renders at build/request
```

**Two-window strategy:** 30-day display window (full details) + 90-day dedup window (just IDs to prevent false-positive winners).

**Dual-strategy winner detection:** `/proposta` endpoint for open bidding proposals + `/atualizacao` endpoint for recently-homologated licitações.

## App Structure

```
src/
├── app/page.tsx                    Server Component entry point
├── components/
│   ├── tab-content.tsx             Route switcher (?tab=garantia|mercado|pipeline)
│   ├── garantia-*                  Winner tab (urgency-weighted scoring)
│   │   ├── garantia-dashboard.tsx  Orchestrator
│   │   ├── garantia-filter-bar.tsx 13-dimension filters
│   │   ├── garantia-table.tsx      Sortable, paginated, expandable
│   │   └── garantia-row-detail.tsx Company detail + WhatsApp + commission calc
│   ├── filter-bar.tsx              Market lead filters
│   ├── lead-table.tsx              Market lead table
│   ├── lead-row-detail.tsx         Expandable row detail
│   └── commission-calc.tsx         Interactive sliders
└── lib/
    ├── types.ts                    Domain types (Lead, GarantiaLead, Empresa, etc.)
    ├── scoring.ts                  Market: value(35) + recency(25) + contact(20) + category(20)
    ├── garantia-scoring.ts         Winners: urgency(40) + value(30) + contact(20) + category(10)
    ├── commission.ts               Commission estimator formula
    ├── constants.ts                Weights, thresholds, API config
    ├── cnae.ts                     CNAE 2.0 → 9-sector classification
    ├── data.ts                     getLeads(), getGarantiaLeads() with caching
    ├── pncp/                       API client, types, link builders
    ├── cnpj/                       Enrichment types, BrasilAPI/Minha Receita mappers
    └── ceis/                       Debarment checker
```

## Key Technical Patterns

- **Resume-safe idempotent pipeline:** Load existing output → skip processed items → add new → save incrementally. Safe to kill and restart. `--fresh` flag for full backfill.
- **Rate limiting with exponential backoff:** 300ms base delay, `2^attempt` multiplier on 429/5xx. Concurrent batching (5 parallel @ 200ms) for Minha Receita.
- **Circuit-breaker:** 5 consecutive failures → 1-minute cooldown. Prevents cascading failures on API outages.
- **LLM edital analysis:** 3-step pipeline (fetch PDF → extract text + keywords → Claude Haiku/Gemini Flash structured extraction). `--dry-run` and `--limit` for testing. Output: guarantee requirements, contract terms, key obligations.
- **Client-side filtering:** 13 filter dimensions applied in React over pre-loaded dataset. Instant responsiveness, no server round-trips. Trade-off: 2K lead cap.

## Performance Considerations

- Static JSON enables instant page loads — no database round-trips
- `CLIENT_LEAD_CAP = 2,000` keeps payload under 5MB for browser rendering
- Pipeline daily incremental: ~15-30 min (vs ~10 hours full backfill)
- `checked-compras.json` timestamp cache: re-check items with no results only after 7 days

## Deployment Architecture

- Vercel free tier hosting with static JSON assets
- Pipeline scripts run locally via `scripts/run-pipeline.sh` (ordered, conditional steps)
- Debarment check conditional on `PORTAL_TRANSPARENCIA_TOKEN` env var
- No persistent server, database, or external services at runtime
