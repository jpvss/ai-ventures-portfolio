# Portfolio — AI Ventures Website

## Project overview
Single-page static HTML portfolio for **AI Ventures**, a software development agency targeting Brazilian enterprises. Positioning: "Do problema ao produto, acelerado por IA" — solves real business problems using AI + data as the method. Used by the commercial team to showcase projects and pitch clients.

## Architecture
- Single HTML file with inline CSS + minimal vanilla JS (~15 lines for scroll reveal and sticky nav)
- Data source: `portfolio-data/portfolio-data.json` (read-only reference, data is hardcoded into HTML)
- Output: `docs/index.html`

## Design direction
- **Editorial / ink-on-paper** — white backgrounds, bold black typography, generous whitespace
- Inspired by minimalist editorial sites (Escola de Dados style)
- Teal (#0D9488) used sparingly as accent (labels, bullets, emphasis words) — never as backgrounds or badges
- No dark hero sections, no gradients — type and whitespace do the heavy lifting

## Key conventions
- Agency name: **AI Ventures**
- All text in Portuguese (pt-BR)
- HTML lang="pt-BR"
- Mobile-first responsive CSS (max-width: 960px for editorial readability)
- Palette: black (#0a0a0a) text + teal (#0D9488) accent + white backgrounds
- Google Fonts: Inter (400-900) via `<link>` tag with system font fallback
- Null JSON fields are omitted (never show "N/A")
- External links use `target="_blank" rel="noopener noreferrer"`
- Projects grouped by value delivered: Market Intelligence (3), Ops & Compliance (3), Growth & Leads (4)
- Each group has a header with label (01/02/03), title, and subtitle explaining the value pattern
- Project cards: full-width (1 per row), problem-focused description + key metric, collapsed `<details>` for full info
- Capabilities bar: cross-cutting technical tags between header and projects
- Opportunities: grouped by macro-segment with count indicators
- Scroll reveal: elements fade in via IntersectionObserver, respects prefers-reduced-motion
- Sticky nav: appears after scrolling past header with backdrop blur

## Placeholders (TODO)
Search for `<!-- TODO:` in index.html to find remaining placeholders:
- Contact email
- WhatsApp number
- OG image URL
- Canonical URL / domain

## File structure
```
.
├── CLAUDE.md
├── .gitignore
├── portfolio-data/
│   └── portfolio-data.json    # Source data (read-only reference)
└── docs/
    └── index.html             # The portfolio site (single file, served by GitHub Pages)
```

## Testing
Open `docs/index.html` directly in a browser. Test at:
- Mobile: 375px width (iPhone SE)
- Tablet: 768px width
- Desktop: 1280px width

Check: all 10 project cards render, opportunities grouped by ~10 macro-segments, all links work, no horizontal overflow on mobile.
