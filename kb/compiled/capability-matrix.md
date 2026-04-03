---
title: "Capability Matrix"
type: compiled
language: en
last_compiled: 2026-04-02
sources:
  - kb/projects/INDEX.md
  - kb/projects/florida-flip/README.md
  - kb/projects/licitaleads/README.md
  - kb/projects/kiiry-dashboard/README.md
  - kb/projects/licenciaminer/README.md
  - kb/projects/leila-do-leilao/README.md
  - kb/projects/ceap-deputy-expenses/README.md
  - kb/projects/deixacomigo/README.md
  - kb/projects/cv10x/README.md
  - kb/projects/kiiry-crm/README.md
  - kb/projects/incorporacoes-gestao/README.md
freshness: quarterly
tags: [capability, matrix, compiled]
---

# Capability Matrix

## Core Capabilities x Projects

| Capability | Projects | Count | Evidence |
|------------|----------|:-----:|----------|
| **Public data ingestion & normalization** | FloridaFlip, LicitaLeads, LicenciaMiner, CEAP, Leila do Leilao | 5 | FloridaFlip: FDOR/FEMA/Census/Redfin pipeline; LicitaLeads: PNCP API + BrasilAPI; LicenciaMiner: 14 simultaneous sources (REST, ArcGIS, Excel, scraping, shapefiles, PDFs); CEAP: Dados Abertos API; Leila: Caixa CSV + ITBI + scraping |
| **Multidimensional scoring engine** | FloridaFlip, LicitaLeads, Leila do Leilao, Kiiry CRM, DeixaComigo | 5 | FloridaFlip: 9-dimension submarket scoring by ZIP; LicitaLeads: 4-dimension composite 0-100 with A/B/C tiers; Leila: Deal Score (discount, occupancy, modality, financing, confidence); Kiiry CRM: 5-axis 0-100 lead score; DeixaComigo: 6-factor consignment aptitude |
| **DuckDB/Parquet analytics** | FloridaFlip, LicenciaMiner, CEAP, Leila do Leilao | 4 | FloridaFlip: 2.1M properties in-browser; LicenciaMiner: materialized views over 12 datasets; CEAP: 660K+ transactions; Leila: Caixa catalog + ITBI cross-reference |
| **Domain-specific financial modeling** | FloridaFlip, Kiiry Dashboard, Leila do Leilao, Incorporacoes Gestao | 4 | FloridaFlip: FL insurance/NFIP/closing costs; Kiiry: CEMIG tariffs/GD I-II/PIS-COFINS; Leila: SAC financing/ITBI/notary; Incorporacoes: Lei 4.591 apportionment with Decimal(15,2) |
| **CNPJ enrichment pipeline** | LicitaLeads, LicenciaMiner, CEAP | 3 | LicitaLeads: BrasilAPI (razao social, phone, email, QSA, CNAE, capital social); LicenciaMiner: Receita Federal cadastral enrichment; CEAP: OpenCNPJ/BrasilAPI with fuzzy matching |
| **Geospatial visualization** | FloridaFlip, LicenciaMiner, Leila do Leilao | 3 | FloridaFlip: Google Maps choropleth by county/ZIP; LicenciaMiner: Folium with ANM concession polygons + UC/TI layers; Leila: Leaflet with Deal Score markers + floating panel |
| **PDF report generation** | FloridaFlip, Kiiry Dashboard, LicenciaMiner, Incorporacoes Gestao | 4 | FloridaFlip: jsPDF executive reports; Kiiry: WeasyPrint investor reports with audit trail; LicenciaMiner: fpdf2 risk dossiers (8 sections); Incorporacoes: @react-pdf apportionment reports |
| **Auditable calculation/reporting** | Kiiry Dashboard, Incorporacoes Gestao | 2 | Kiiry: tooltips with formulas + per-plant audit JSON + diff panel; Incorporacoes: Decimal precision + remainder distribution + persistent audit log |
| **Regulatory compliance modeling** | LicitaLeads, Kiiry Dashboard, LicenciaMiner, Kiiry CRM, Incorporacoes Gestao | 5 | LicitaLeads: Lei 14.133 guarantee categories; Kiiry: CEMIG GD I/II rules; LicenciaMiner: ANM/IBAMA/SEMAD regulatory risk; Kiiry CRM: CEMIG tariff A/B classification; Incorporacoes: Lei 4.591/64 apportionment |
| **Lead generation funnel** | DeixaComigo, CV10x, LicitaLeads | 3 | DeixaComigo: valuation tool to lead capture with email notification; CV10x: free analysis to email gate to Pro upsell; LicitaLeads: pre-filled WhatsApp/call/email per lead |
| **LLM integration** | CV10x, LicenciaMiner | 2 | CV10x: Claude structured output with Zod schemas + iterative prompts + retries; LicenciaMiner: Anthropic SDK for regulatory analysis |
| **Statistical anomaly/fraud detection** | CEAP | 1 | CEAP: Benford's Law, HHI concentration, round value analysis, CNAE mismatch detection on 660K+ transactions |
| **Cross-database fuzzy matching** | CEAP | 1 | CEAP: Fuzzy name matching + identifier normalization for CEAP x Amendments cross-reference |
| **External API caching & enrichment** | DeixaComigo, Kiiry CRM | 2 | DeixaComigo: FIPE/Parallelum API with Supabase cache layer; Kiiry CRM: Google Places API with dedup and enrichment |
| **B2C conversion funnel** | CV10x, DeixaComigo | 2 | CV10x: free tier -> email gate -> nurture -> Pro upsell -> Hotmart payment; DeixaComigo: valuation -> lead capture -> broker notification |
| **Marketing automation** | CV10x | 1 | CV10x: GitHub Actions cron, Redis nurture queue, batch email, Meta CAPI + Google Ads tracking, UTM attribution |
| **Multi-tenant access control** | Incorporacoes Gestao | 1 | Incorporacoes: 3-layer RBAC (middleware + Server Actions + query scoping) with financial data isolation |
| **Engineering document processing** | Incorporacoes Gestao | 1 | Incorporacoes: DWG->DXF conversion, architectural metadata extraction, interactive floor plan + 3D Three.js viewer |
| **Geospatial analysis (spatial joins)** | LicenciaMiner | 1 | LicenciaMiner: GeoPandas/Shapely spatial joins between mining concessions and environmental restriction areas |
| **CRM/pipeline management** | Kiiry CRM | 1 | Kiiry CRM: 8-stage Kanban, multi-territory team management, activity leaderboard, chain/franchise detection |
| **Programmatic SEO** | DeixaComigo | 1 | DeixaComigo: dynamic sitemap, robots.txt, Schema.org, dynamic OpenGraph, architecture for hundreds of model/year pages |

## Capability Depth Summary

| Depth Level | Capabilities | Description |
|-------------|:------------:|-------------|
| **Deep (4--5 projects)** | 5 | Public data ingestion, scoring engines, DuckDB/Parquet, financial modeling, regulatory compliance |
| **Established (2--3 projects)** | 7 | CNPJ enrichment, geospatial viz, PDF generation, lead funnels, API caching, B2C funnels, LLM integration |
| **Demonstrated (1 project)** | 8 | Fraud detection, fuzzy matching, marketing automation, RBAC, DWG processing, spatial joins, CRM, programmatic SEO |
| **Total unique capabilities** | **20** | |
