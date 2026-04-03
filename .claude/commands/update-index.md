Regenerate all INDEX.md files in the knowledge base.

Steps:
1. Scan the full kb/ directory structure
2. For each vertical in kb/verticals/:
   - Count files, check last_compiled dates from frontmatter
   - Update the vertical's README.md file index table
3. For kb/patterns/:
   - List all patterns with their applies_to verticals
   - Regenerate kb/patterns/INDEX.md
4. For kb/projects/:
   - List all projects with their vertical relevance and status
   - Cross-reference with portfolio-data.json for metadata
   - Regenerate kb/projects/INDEX.md
5. Regenerate the master kb/INDEX.md:
   - Update Quick Navigation table
   - Update Verticals table with file counts and last updated dates
   - Update Cross-Vertical Patterns table
   - Update Projects table
   - Update KB Statistics at the bottom
6. Append to kb/CHANGELOG.md
