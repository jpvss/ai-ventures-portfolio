---
title: "LicitaLeads — Reusable Assets"
type: project
slug: licitaleads
language: en
last_compiled: 2026-04-02
---

# LicitaLeads — Reusable Assets

## Component Library (shadcn/ui-based)

- **FilterSelect:** Reusable dropdown with multi-select support for data exploration dashboards
- **SortableHead / SortIcon:** Table header sorting UI with direction indicators
- **Pagination:** Page navigation component (PAGE_SIZE = 50)
- **TierDot / ScoreBadge:** Color-coded status badge rendering for scored items
- **DetailPrimitives (SectionTitle, DT, CopyButton):** Expandable detail view building blocks
- **CommissionCalc:** Interactive slider-based calculator — adaptable for any commission formula

## Utility Modules

| Module | Functions | Reusability |
|---|---|---|
| `lib/phone.ts` | `formatPhone()`, `phoneTelHref()`, `isValidPhone()`, `isDistinctPhone2()` | Any Brazilian B2B app needing phone handling |
| `lib/validators.ts` | `formatCnpj()`, `normalizeCnpj()`, `cnpjSchema` (Zod) | Any app working with CNPJ data |
| `lib/dates.ts` | `formatDateBR()`, `timeAgo()`, `computeDiasSince()` | Any pt-BR application |
| `lib/cnae.ts` | `classifyCnae()`, `getCnaeLabel()` — CNAE 2.0 → 9 sector groups | B2B products needing industry classification |
| `lib/pncp/links.ts` | `buildContratoLink()`, `buildLicitacaoLink()`, `parseCompraControlNumber()` | Any PNCP-integrated application |
| `lib/cnpj/mappers.ts` | `mapBrasilApiToEmpresa()` — API response → domain type | Brazilian B2B enrichment pipelines |

## Pipeline Templates

- **Resume-safe batch fetch:** Load existing → skip processed → add new → save incrementally. Pattern used in all 9 scripts. Reusable for any paginated API ingestion.
- **Rate-limiting with exponential backoff:** 300ms base, `2^attempt` multiplier, circuit-breaker (5 failures → 1-min cooldown). Template for resilient API consumption.
- **Concurrent batching with delays:** 5 parallel requests @ 200ms delay = ~4-5 req/sec. Balances throughput vs rate limits.
- **LLM batch analysis with caching:** Fetch documents → extract text → keyword filter → LLM structured extraction. `--dry-run`, `--limit`, `--max-age` flags. Cost-transparent.
- **Pipeline orchestrator (`run-pipeline.sh`):** Ordered multi-step execution with conditional steps, error tracking, colored output, ETA calculation.

## Domain Types (extractable)

Clean domain-driven types that separate pipeline stages:
- `Contrato` — Raw signed contract from PNCP
- `Adjudicacao` — Winner result (intermediate, becomes contract)
- `GarantiaLead` — Denormalized winner with enrichment (final output)
- `Lead` — Denormalized signed contract with enrichment (final output)
- `Empresa` — CNPJ enrichment data (razão social, phone, QSA, CNAE, porte, capital)
- `EditalAnalysis` — LLM-extracted edital intelligence (guarantee, contract terms, requirements)

## WhatsApp Integration

- `buildWhatsAppLink()` utility with phone validation and +55 country code
- Two message templates (market leads vs garantia winners) with dynamic contract data
- Graceful fallback on invalid phone numbers

## Patterns That Map to kb/patterns/

| Asset | Related Pattern |
|---|---|
| PNCP ingestion pipeline | `kb/patterns/data-integration.md` |
| CNPJ enrichment module | `kb/patterns/data-integration.md` |
| CEIS/CNEP compliance checker | `kb/patterns/compliance-automation.md` |
| Composite scoring engine | `kb/patterns/predictive-models.md` |
| Edital LLM analysis pipeline | `kb/patterns/document-intelligence.md` |
| High-density filter dashboard | `kb/patterns/client-360.md` |

## Data Sources and Integrations

| Source | Purpose | Access |
|---|---|---|
| PNCP API | Public contracts, bids, winners | Public REST API |
| BrasilAPI / Minha Receita | CNPJ enrichment (business data) | Public API, rate-limited |
| Portal da Transparência / CGU | CEIS/CNEP ineligibility lists | API with token |
| SUSEP data | Insurance market reference | Public datasets |
