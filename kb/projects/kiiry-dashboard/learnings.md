---
title: "Kiiry Dashboard — Learnings"
type: project
slug: kiiry-dashboard
language: en
last_compiled: 2026-04-02
---

# Kiiry Dashboard — Learnings

## What Worked Well

- **Complete audit trail with formula traceability** — Every financial calculation exposes its formula, source values, and rounding decisions via tooltips and per-plant/month audit JSON, making the system compliance-ready for investor scrutiny and eliminating "black box" objections from stakeholders.
- **Multi-source Excel ETL with Pandas** — Ingesting heterogeneous multi-tab CEMIG Excel files alongside Cogni invoices/boletos/UCs through a single normalization pipeline with aliasing and cross-validation proved robust despite wildly inconsistent source formats.
- **WeasyPrint for investor-grade PDF reports** — Generating professional PDF reports with built-in audit trails via WeasyPrint + Jinja2 templates delivered investor-ready documents that replaced manual Excel-to-PDF workflows prone to formatting errors.
- **Zero-database architecture on Railway** — Running the entire platform with in-memory cache and no persistent database simplified deployment to a git-push continuous deploy model, keeping infrastructure costs minimal for a small-plant solar portfolio.
- **Domain-specific payment status management** — Modeling 5 distinct payment states (PAGO, Inadimplente, Em Aberto, Nao Emitido, Inadimplente Anterior) with solar-sector-specific transition rules captured business logic that generic accounting tools miss entirely.

## Challenges Encountered

- **CEMIG data format instability** — CEMIG Excel exports change column names, tab structures, and date formats between billing periods, requiring defensive parsing with fallback column matching and extensive logging to catch silent ingestion failures.
- **GD I/II compensable tariff complexity** — Calculating dynamic compensable tariffs under Brazil's distributed generation regulatory framework (GD I vs. GD II rules, PIS/COFINS, ICMS, Fio B components) required deep regulatory research and ongoing updates as ANEEL adjusts rules.
- **Delinquency classification edge cases** — Distinguishing between "invoice not yet issued by Cogni" vs. "invoice issued but unpaid" vs. "historically delinquent" required multi-source cross-referencing with temporal logic that simple status flags could not capture.
- **WeasyPrint rendering consistency** — WeasyPrint's CSS rendering differs from browser rendering, requiring a separate CSS tuning pass for PDF output to ensure tables, page breaks, and financial figures render correctly in printed form.

## Key Technical Decisions

- **Flask + Pandas over Django/FastAPI** — Chose Flask for its minimal footprint and Pandas for its Excel handling strength, prioritizing rapid development of a data-heavy internal tool over API-first architecture — the right trade-off for a single-client platform with no external API consumers.
- **Pydantic v2 for data validation** — Used Pydantic models to validate every ingested record from CEMIG and Cogni, catching data quality issues at ingestion time rather than allowing them to propagate into financial calculations — critical when cent-level errors affect real investor payments.
- **TOML configuration over environment variables** — Stored plant-specific configuration (tariff parameters, UC mappings, commission rates) in TOML files rather than env vars, enabling version-controlled, auditable configuration changes that can be reviewed before deployment.
- **Structured logging with structlog** — Implemented structured JSON logging throughout the ETL pipeline, enabling rapid diagnosis of ingestion failures across multiple plants and billing periods without manual log parsing.

## Business Impact

- **Eliminated manual reconciliation for active solar portfolio** — Replaced a multi-hour monthly process of cross-referencing CEMIG bills with Cogni invoices, reducing report preparation time from days to minutes and eliminating cent-level apportionment errors that caused investor disputes.
- **Proved the "auditable financial reporting" pattern** — Demonstrated that financial reporting systems for regulated sectors must embed audit trails at the calculation level, not just the document level — a pattern directly applicable to insurance-surety accountability, mining royalty reporting, and investment fund NAV calculation.
- **Validated serverless deployment for internal tools** — Showed that Railway's git-push deploy model is viable for financial tools serving small user bases (plant managers, investors), keeping monthly infrastructure costs under R$ 50 while maintaining professional-grade reliability.
- **Built reusable ETL patterns for Brazilian regulated sectors** — The CEMIG/Cogni ingestion pipeline established patterns for handling Brazil's idiosyncratic government and utility data formats — reusable for ANEEL, ANM, SUSEP, and municipal data sources across verticals.
