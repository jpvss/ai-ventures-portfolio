Generate a compiled report from the knowledge base.

Arguments: $ARGUMENTS (report type)

Available report types:
- "vertical-summary {name}" — One-pager summary of a specific vertical
- "cross-vertical" — Analysis of patterns and opportunities across all verticals
- "capability-matrix" — What we can do, mapped to evidence from projects and verticals
- "portfolio-digest" — All projects summarized for quick reference
- "sales-brief {vertical}" — Sales-ready brief for a specific vertical with hooks, pricing, and proof points

Steps:
1. Read all relevant source files for the requested report type
2. Synthesize content following a clear, structured format
3. Write output to kb/compiled/{report-name}.md
4. Update frontmatter with compilation timestamp
5. Append to kb/CHANGELOG.md
6. Display a summary of what was generated
