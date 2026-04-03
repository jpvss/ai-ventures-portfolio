Lint the knowledge base for consistency, completeness, and data integrity.

Run all checks and report findings as a checklist with severity (ERROR/WARNING/INFO).

Checks:
1. STRUCTURE: Verify every vertical has all 9 standard files matching _template/ structure
2. FRONTMATTER: Check all KB files have valid YAML frontmatter with required fields (title, type, vertical, language, last_compiled, sources, freshness, tags)
3. CROSS-REFERENCES: Verify all relative path links in KB files resolve to existing files
4. FRESHNESS: Flag content where last_compiled is older than the freshness interval (monthly > 30 days, quarterly > 90 days, annual > 365 days)
5. INDEX SYNC: Verify kb/INDEX.md matches actual directory structure and file counts
6. PROJECT COVERAGE: Verify every project in portfolio-data.json has a corresponding kb/projects/{slug}/ directory
7. DUPLICATION: Check for content that appears in multiple vertical files but should be in kb/patterns/ instead
8. LANGUAGE: Verify internal KB files are in English, docs/ files are in Portuguese (pt-BR)
9. EMPTY FILES: Flag any KB files that are still template-only (contain placeholder text like {VERTICAL_NAME})
10. CHANGELOG: Verify kb/CHANGELOG.md exists and has recent entries

Report format:
```
## KB Lint Report — YYYY-MM-DD

### Errors (must fix)
- [ ] ...

### Warnings (should fix)
- [ ] ...

### Info (nice to know)
- [ ] ...

### Summary
X errors, Y warnings, Z info items
```
