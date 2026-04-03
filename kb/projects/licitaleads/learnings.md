---
title: "LicitaLeads — Learnings"
type: project
slug: licitaleads
language: en
last_compiled: 2026-04-02
---

# LicitaLeads — Learnings

## What Worked Well

- **Two-window contract deduplication:** 30-day display window for manageable UI + 90-day dedup cache to prevent false-positive winners. Elegant trade-off between freshness and accuracy.
- **Dual-strategy winner detection:** `/proposta` endpoint for open bidding + `/atualizacao` endpoint for recently-homologated results. Solves the "missing winners" problem where homologation happens weeks after proposal close.
- **Resume-safe pipeline with incremental caching:** All scripts check existing output, skip processed items, and save progress every N records. `fetch-resultados.ts` timestamps checked compras and re-checks after 7 days. Daily runs take ~15-30 min vs ~10 hours for full backfill.
- **Static JSON architecture for MVP validation:** Zero database costs, instant page loads, Vercel free tier deployment. Current data volume (23K leads, ~8MB) fits comfortably. Allowed shipping product without infrastructure decisions.
- **Urgency-weighted scoring for garantia tab:** Prioritizes days-since-resultado (0-3 days = max score) over publication recency. Matches broker workflow: winners TODAY need seguro garantia ASAP.
- **WhatsApp deep links with pre-filled messages:** Two versions (market leads vs garantia winners) with dynamic contract value and object description. ~88% phone coverage enables immediate contact.
- **CNAE 2.0 sector classification:** Pure function mapping 7-digit CNAE fiscal codes → 9 sector groups. Extensible and reusable across any Brazilian B2B product.

## Challenges Encountered

- **PNCP API limitations:** No bulk winner endpoint — winner detection requires per-item API calls. Slow API (~300ms/page) with modest page sizes (50 max for contratações). No official rate limit documentation; relied on 300ms delay + exponential backoff.
- **Email field always null:** Minha Receita API returns null email consistently (Receita Federal limitation). Brokers must fall back to phone contact. No workaround found.
- **Vercel serverless size limits:** Had to implement `CLIENT_LEAD_CAP = 2,000` to keep JSON payload under 5MB for browser rendering. Top 2K leads by score; lower-scored leads invisible in initial HTML.
- **QSA field mapping bug:** `qual_socio ≠ qualificacao_socio` in enrichment response caused role data loss. Required `--refresh-qsa` flag to re-fetch affected records.
- **Porte (company size) normalization:** Raw PNCP data has inconsistent encoding ("MICRO EMPRESA" vs "ME" vs "MICRO"). Required manual normalization function.
- **Edital PDF extraction fragility:** PDFs can be password-protected, scanned images, or DOCX format. Keyword filtering before LLM analysis reduces cost but is lossy.
- **No cross-tab context:** "Garantia" (winners) and "Mercado" (open licitações) are separate datasets with no linking to see which winners came from which open processes.

## Key Technical Decisions

- **Static JSON over database:** Chose pre-computed JSON files served as static assets. Rationale: zero infrastructure cost during validation phase, instant page loads, pipeline runs as batch process. Trade-off: data freshness depends on pipeline re-runs + redeploy.
- **Client-side filtering over server-side:** All 13 filter dimensions applied in React after data loads. Rationale: instant responsiveness, no server round-trips. Trade-off: limited to 2K leads in initial HTML.
- **Two scoring systems (market vs garantia):** Market leads weight value (35%) + recency (25%) + contact (20%) + category (20%). Garantia leads weight urgency (40%) + value (30%) + contact (20%) + category (10%). Different use cases demand different prioritization.
- **Guarantee percentage estimation by tier/category:** Hardcoded tiers (30% for high-value engineering, 10% for tier A, 5% default). Simplistic but functional until edital LLM analysis provides actual percentages.
- **LLM edital analysis with cost transparency:** Supports Claude Haiku and Gemini Flash. Incremental cost ~$0.40/day (Claude) or ~$0.04 (Gemini). `--dry-run` and `--limit` flags for safe testing.
- **Circuit-breaker for API resilience:** 5 consecutive failures trigger 1-minute cooldown (Minha Receita). Prevents cascading failures on API outages.

## Business Impact

- **23K+ contracts ingested** from PNCP with automated enrichment (CNPJ, phone, QSA, CNAE, debarment checks)
- **Composite scoring** enables brokers to focus on highest-value opportunities instead of manual portal scanning
- **Commission calculator** with interactive sliders gives brokers instant "what-if" analysis for each lead
- **Pipeline runs daily** with incremental updates, keeping data fresh with minimal compute
- **Zero infrastructure cost** during MVP phase — entire product runs on Vercel free tier + local scripts
- **Edital intelligence pipeline** extracts guarantee requirements from PDF documents using LLM, enabling more accurate commission estimates
