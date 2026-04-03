---
title: "Portfolio Digest"
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
tags: [portfolio, digest, compiled]
---

# Portfolio Digest

**10 projects** | **20 unique capabilities** | **4 verticals + adjacent**

---

## Market Intelligence (4 projects)

### FloridaFlip
Real estate investors waste hours cross-referencing public data to find opportunities. FloridaFlip aggregates 2.1M+ Florida properties from FDOR, FEMA, Census, and Redfin into a DuckDB/Parquet-powered dashboard with choropleth maps, a 9-dimension submarket scoring engine, and flip/hold/BRRRR financial calculators with Florida-specific regulatory rules.
**Vertical:** investment-advisory | **Status:** Deployed

### LicenciaMiner
Environmental consultancies spend weeks manually searching IBAMA, ANM, and SEMAD portals to assess mining license feasibility. LicenciaMiner fuses 14 public sources (REST APIs, ArcGIS, Excel, HTML scraping, shapefiles, PDFs) into an analytical dashboard with CNPJ dossiers, spatial overlap detection between mining concessions and environmental restrictions, and professional PDF risk reports.
**Vertical:** mining | **Status:** Local/Container

### Leila do Leilao
Caixa auction investors cannot determine true property discounts because appraisals do not reflect market price. Leila cross-references real ITBI transaction data (2008--2026) with the Caixa catalog, computing a multidimensional Deal Score per property, with interactive maps, financial simulators (SAC financing, municipality-specific ITBI), and risk flags (liens, favelas).
**Vertical:** auctions | **Status:** Not deployed

### CEAP Dashboard
Citizens and journalists cannot cross-reference R$686M in parliamentary expenses with budget amendments to identify corruption. The dashboard applies statistical fraud detection (Benford's Law, HHI, CNAE mismatch) across 660K+ transactions from 847 deputies, with D3.js visualizations, investigative cross-references, and CNPJ enrichment.
**Vertical:** adjacent | **Status:** Deployed

---

## Ops & Compliance (3 projects)

### LicitaLeads
Surety bond brokers waste hours scouring the PNCP portal for contracts requiring guarantees. LicitaLeads ingests ~23K public contracts, enriches them with CNPJ data (BrasilAPI), scores leads 0--100 across 4 dimensions, and delivers a high-density dashboard with 11 filters, pre-filled WhatsApp/call/email actions, and commission calculators -- all on zero infrastructure (static JSON, Vercel free tier).
**Vertical:** insurance-surety | **Status:** Deployed

### Kiiry Dashboard
Solar plant owners need monthly investor accountability reports reconciling CEMIG energy data with Cogni billing. Kiiry automates the entire pipeline -- multi-source Excel ETL, dynamic tariff calculations (GD I/II, PIS/COFINS, ICMS), delinquency classification -- and generates auditable PDF reports with complete formula traceability and per-plant audit JSON.
**Vertical:** investment-advisory | **Status:** Deployed

### Incorporacoes Gestao
Condominial real estate development investor groups depend on manual spreadsheets for proportional expense apportionment by ideal fraction. This platform provides Decimal(15,2) precision financial apportionment per Lei 4.591/64, 3-layer RBAC isolating investor data, DWG/DXF floor plan processing with interactive rendering, and Three.js 3D model visualization.
**Vertical:** investment-advisory | **Status:** Deployed

---

## Growth & Leads (3 projects)

### DeixaComigo
Premium used car owners are lowballed by dealers paying 75--85% of FIPE. DeixaComigo shows the concrete difference between dealer and consignment pricing via a FIPE-integrated valuation engine with 6 calibrated factors, converting car owners into qualified leads with automatic broker notification (Resend), Supabase persistence, and programmatic SEO for organic traffic.
**Vertical:** adjacent | **Status:** Deployed

### CV10x
Data professionals in Brazil send resumes with no feedback on competitiveness. CV10x uses Claude AI to analyze resumes across 5 dimensions (Technical, Impact, Structure, ATS, Narrative), gates the full report behind email capture, and upsells a Pro plan with personalized rewrites, job matching, and an automated 5-email nurture sequence powered by GitHub Actions cron jobs and Redis queues.
**Vertical:** adjacent | **Status:** Deployed

### Kiiry CRM
Solar energy sales teams spend hours manually searching for commercial leads and cannot prioritize prospects. Kiiry CRM automates lead capture via Google Places API with intelligent deduplication, scores leads 0--100 across 5 axes (energy potential, size, ICP fit, credibility, reachability), and organizes an 8-stage Kanban pipeline for 8+ simultaneous salespeople with territory management.
**Vertical:** adjacent | **Status:** Deployed

---

## Summary Statistics

### Capabilities Demonstrated: 20

| Depth | Count | Examples |
|-------|:-----:|---------|
| Deep (4--5 projects) | 5 | Public data ingestion, scoring engines, DuckDB/Parquet, financial modeling, regulatory compliance |
| Established (2--3 projects) | 7 | CNPJ enrichment, geospatial visualization, PDF generation, lead funnels, LLM integration |
| Demonstrated (1 project) | 8 | Fraud detection, marketing automation, RBAC, DWG processing, spatial joins, CRM |

### Vertical Coverage Map

| Vertical | Projects | Primary Evidence |
|----------|:--------:|-----------------|
| Mining | 1 | LicenciaMiner |
| Investment Advisory | 3 | FloridaFlip, Kiiry Dashboard, Incorporacoes Gestao |
| Insurance/Surety Bonds | 1 | LicitaLeads |
| Auctions | 1 | Leila do Leilao |
| Adjacent | 4 | CEAP, DeixaComigo, CV10x, Kiiry CRM |

### Deployment Status

| Status | Count | Projects |
|--------|:-----:|---------|
| Deployed | 8 | FloridaFlip, LicitaLeads, Kiiry Dashboard, CEAP, DeixaComigo, CV10x, Kiiry CRM, Incorporacoes Gestao |
| Local/Container | 1 | LicenciaMiner |
| Not deployed | 1 | Leila do Leilao |

### Tech Stack Patterns

| Technology | Usage Count | Role |
|-----------|:-----------:|------|
| Next.js | 7 | Full-stack framework |
| TypeScript | 9 | Type safety |
| Tailwind CSS | 9 | Styling |
| DuckDB/Parquet | 4 | Analytical queries |
| Python | 5 | Data pipelines |
| Supabase | 3 | Database/auth |
| Vercel | 7 | Deployment |
