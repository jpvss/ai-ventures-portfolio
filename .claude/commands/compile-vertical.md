Compile or recompile a vertical's knowledge base files from raw sources.

Arguments: $ARGUMENTS (vertical name, e.g., "mining", "investment-advisory", "insurance-surety", "auctions")

Steps:
1. Read all files in kb/raw/ that are tagged for this vertical (check frontmatter tags)
2. Read the current state of all 9 files in kb/verticals/{vertical}/
3. For each of the 9 standard files (README.md, market-context.md, regulatory-map.md, solution-patterns.md, engagement-templates.md, competitive-intel.md, case-studies.md, sales-playbook.md, tech-landscape.md):
   a. Extract relevant content from raw sources
   b. Merge with existing content (preserve manually-added insights, don't overwrite)
   c. Update the frontmatter last_compiled date
   d. Ensure cross-references to kb/patterns/ are current
4. Regenerate kb/compiled/vertical-summaries/{vertical}-summary.md
5. Update kb/verticals/{vertical}/README.md with current statistics
6. Update kb/INDEX.md
7. Append changes to kb/CHANGELOG.md
