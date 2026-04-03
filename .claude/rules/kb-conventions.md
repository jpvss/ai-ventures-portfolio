## KB Conventions

### File Naming
- All lowercase, hyphens for spaces: `market-context.md`, not `Market Context.md`
- Vertical directories: singular noun or compound: `mining/`, `insurance-surety/`
- Raw research files: `YYYY-MM-{topic-slug}.md`
- Engagement notes: `YYYY-MM-{client-slug}-{engagement-type}.md`
- Project directories: match portfolio-data.json slug field

### YAML Frontmatter (Required on Every KB File)
Every markdown file in kb/ MUST start with YAML frontmatter containing at minimum:
- title, type, vertical, language, last_compiled, sources, freshness, tags

### Vertical Structure
Every vertical MUST have exactly these 9 files:
1. README.md — Overview and statistics
2. market-context.md — Market size, players, trends
3. regulatory-map.md — Agencies, laws, compliance
4. solution-patterns.md — Technical patterns for this vertical
5. engagement-templates.md — Diagnostic + implementation playbooks
6. competitive-intel.md — Competitors, pricing
7. case-studies.md — Anonymized outcomes
8. sales-playbook.md — Hooks, objection handling, pricing
9. tech-landscape.md — Systems, APIs, integrations

### Cross-References
- Use relative paths from repo root: `kb/patterns/compliance-automation.md`
- When a pattern applies to 2+ verticals, it belongs in kb/patterns/, not duplicated
- Vertical solution-patterns.md files SHOULD reference the canonical pattern in kb/patterns/

### Content Principles
- Be specific and quantified: use numbers, dates, law references, not vague claims
- Source everything: every fact should trace back to a raw/ document or external source
- Keep files focused: one topic per file, link to related files rather than duplicating
- Compiled files are output: regenerate rather than manually edit kb/compiled/
