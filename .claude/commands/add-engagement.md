Record engagement notes and extract reusable learnings into the knowledge base.

Arguments: $ARGUMENTS (engagement description — client type, vertical, what was done, outcomes)

Steps:
1. Create raw engagement notes in kb/raw/engagement-notes/ with naming: YYYY-MM-{client-slug}-{type}.md
2. Add frontmatter with date, vertical, engagement type, and anonymized client description
3. Extract and categorize learnings:
   - Architecture decisions → kb/projects/{slug}/architecture.md (if related to a portfolio project)
   - Reusable technical patterns → kb/patterns/ (create new or update existing)
   - Vertical intelligence → kb/verticals/{vertical}/ (update the appropriate files)
   - Sales/competitive insights → kb/verticals/{vertical}/competitive-intel.md or sales-playbook.md
   - Quantified outcomes → kb/verticals/{vertical}/case-studies.md (anonymized)
4. If anonymizable outcomes exist, create or update a case study entry
5. Append to kb/CHANGELOG.md
6. Report what was extracted and where it was filed
