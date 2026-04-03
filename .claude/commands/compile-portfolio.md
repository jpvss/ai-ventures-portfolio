Generate public-facing HTML pages from KB content for GitHub Pages.

Arguments: $ARGUMENTS (optional: "all", specific vertical name, specific project slug)

Steps:
1. Read docs/index.html for the existing design system (CSS, fonts, layout patterns)
2. If "all" or a vertical name:
   a. Read kb/verticals/{name}/README.md + market-context.md + sales-playbook.md + solution-patterns.md
   b. Generate docs/verticals/{name-pt-br}.html following the editorial design (white, black, teal accent, Inter font, 960px max-width)
   c. Content must be in Portuguese (pt-BR) with lang="pt-BR"
   d. Include: market overview, capabilities, engagement types, related projects, contact CTA
   e. Link back to docs/index.html and cross-link to related vertical/project pages
3. If "all" or a project slug:
   a. Read portfolio-data.json for project metadata + kb/projects/{slug}/README.md
   b. Generate docs/projetos/{slug}.html following the same design system
   c. Content in Portuguese (pt-BR)
   d. Include: problem, solution, stack, capabilities, related opportunities
4. If "all":
   a. Update docs/index.html navigation to link to all vertical and project pages
5. Verify: no broken links, correct lang attribute, responsive at 375px/768px/1280px

Mapping:
- mining → docs/verticals/mineracao.html
- investment-advisory → docs/verticals/investimentos.html
- insurance-surety → docs/verticals/seguros.html
- auctions → docs/verticals/leiloes.html
