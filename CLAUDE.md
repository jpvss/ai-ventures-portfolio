# JP Ventures — Portfolio + Knowledge Base

## Project Overview
JP Ventures portfolio site (GitHub Pages) + consulting knowledge base (GenAI-native).
3-person AI-native data infrastructure consulting agency targeting Brazilian mid-market.
4 verticals: Mining, Investment Advisory, Insurance/Surety Bonds, Auctions.

## Architecture
- `docs/` — GitHub Pages output (static HTML, pt-BR client-facing)
- `kb/` — Consulting knowledge base (Markdown + YAML frontmatter, English internal)
- `portfolio-data/portfolio-data.json` — Structured project data (source of truth for projects)
- `kb/raw/` — Source documents for LLM compilation (never edited after ingestion)
- `kb/verticals/` — 4 industry verticals with 9 standardized files each
- `kb/patterns/` — Cross-vertical reusable solution patterns
- `kb/projects/` — Per-project learnings and architecture decisions
- `kb/agency/` — Agency operations, positioning, pricing
- `kb/compiled/` — LLM-generated summaries and analyses (output only, regenerate don't edit)

## Compilation Flow
```
raw/ → verticals/ + patterns/ + projects/ → compiled/ → docs/
```

## KB Navigation
Start at `kb/INDEX.md` for the master index. Each vertical has 9 files:
README.md, market-context.md, regulatory-map.md, solution-patterns.md,
engagement-templates.md, competitive-intel.md, case-studies.md, sales-playbook.md, tech-landscape.md

## KB Maintenance Commands
- `/project:add-research` — Add new research to raw/ and update relevant verticals
- `/project:compile-vertical` — Recompile a vertical's files from raw sources
- `/project:lint-kb` — Check KB consistency, broken links, stale metadata
- `/project:generate-report` — Generate compiled output (summary, analysis, matrix)
- `/project:add-engagement` — Record engagement notes, extract learnings into KB
- `/project:update-index` — Regenerate all INDEX.md files
- `/project:compile-portfolio` — Generate docs/ HTML pages from KB content

## Key Conventions
- Agency name: **JP Ventures**
- Internal KB: English. Public docs/: Portuguese (pt-BR), lang="pt-BR"
- YAML frontmatter required on every kb/ markdown file
- File names: lowercase, hyphens, no spaces
- Cross-references use relative paths from repo root
- portfolio-data.json is source of truth for project metadata
- Brazilian regulatory terms stay in Portuguese even in English docs (CFEM, LGPD, etc.)
- Currency: always R$ not BRL

## Portfolio Site Design
- Editorial / ink-on-paper: white backgrounds, bold black typography, generous whitespace
- Teal (#0D9488) accent, Inter font, max-width 960px
- Mobile-first responsive (375px / 768px / 1280px breakpoints)
- Projects grouped by value: Market Intelligence, Ops & Compliance, Growth & Leads

## File Relationships
- portfolio-data.json → docs/index.html (projects section)
- kb/verticals/*/README.md → docs/verticals/*.html (vertical pages)
- kb/projects/*/README.md → docs/projetos/*.html (project detail pages)
- kb/raw/* → kb/verticals/* (source → compiled)

## When Compacting
Preserve: current vertical count (4), last compilation date, any in-progress KB edits, which raw sources have been processed.

## Placeholders (TODO)
Search for `<!-- TODO:` in docs/ HTML files for remaining placeholders.
