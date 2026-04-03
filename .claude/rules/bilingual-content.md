## Bilingual Content Rules

### Language Assignment
- `kb/` internal files: English (en)
- `docs/` public pages: Portuguese (pt-BR)
- `portfolio-data/portfolio-data.json`: Portuguese (pt-BR) — existing convention
- `CLAUDE.md`, `.claude/`: English (en)

### Exceptions (Portuguese Terms in English Docs)
Keep in Portuguese even in English KB files:
- Brazilian regulatory terms: CFEM, LGPD, SUSEP, CVM, ANM
- Law references: Lei 14.133/2021, Circular SUSEP 662/2022
- Agency names: Agência Nacional de Mineração, Comissão de Valores Mobiliários
- Currency: R$ (Real), always use R$ not BRL
- Industry-specific terms: leiloeiro, edital, matrícula, condicionante, seguro garantia
- Company names: keep original language

### HTML Pages (docs/)
- Always set `lang="pt-BR"` on the html tag
- All user-facing text in Portuguese
- Technical terms (API, SQL, ML) can remain in English
- Use Brazilian date format: DD/MM/YYYY
- Use Brazilian number format: 1.000,00 (period for thousands, comma for decimal)
