Add new research to the knowledge base.

Arguments: $ARGUMENTS

Steps:
1. Read the provided research content, URL, or file path
2. If a URL is provided, use WebFetch to retrieve the content
3. Determine which vertical(s) and pattern(s) the research relates to
4. Create a new file in kb/raw/research/ with naming: YYYY-MM-{topic-slug}.md
5. Add YAML frontmatter with date, source URL/path, and vertical tags
6. For each affected vertical, read the relevant files (market-context.md, regulatory-map.md, etc.) and integrate the new information
7. Update kb/INDEX.md if structural changes occurred
8. Append the addition to kb/CHANGELOG.md with date and summary
9. Report what was added and which files were updated
