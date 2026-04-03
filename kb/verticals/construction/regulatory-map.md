---
title: "Construction — Regulatory Map"
type: regulatory-map
vertical: construction
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: monthly
tags: [construction, regulatory, compliance, SINAPI, NR-18, BIM, Lei-14133]
---

# Construction — Regulatory Map

## Regulatory Bodies

| Agency | Jurisdiction | Key Role | Website |
|--------|-------------|----------|---------|
| **Caixa Economica Federal** | SINAPI reference costs | Publishes and maintains SINAPI cost system — mandatory for Caixa-funded projects | caixa.gov.br |
| **DNIT** (Departamento Nacional de Infraestrutura de Transportes) | SICRO reference costs | Publishes SICRO cost system — mandatory for DNIT infrastructure projects | dnit.gov.br |
| **Sinduscon** (state-level) | CUB reference costs | Publishes monthly CUB (Custo Unitario Basico) per m2 by state — used for contract indexation | sinduscon.org.br |
| **MTE** (Ministerio do Trabalho e Emprego) | Labor safety (NRs) | Enforces NR-18 (construction safety) and other labor safety norms | gov.br/trabalho |
| **IBAMA / State Environmental Agencies** | Environmental licensing | Environmental permits for construction projects with significant impact | ibama.gov.br |
| **Prefeituras Municipais** (5,570) | Building permits, habite-se | Issue alvaras de construcao, habite-se certificates, and enforce local building codes | Varies by municipality |
| **CONFEA/CREA** | Engineering oversight | Professional regulation for engineers and architects; technical responsibility (ART) | confea.org.br |
| **ABNT** | Technical norms (NBRs) | Publishes NBR construction norms (structural, electrical, plumbing, fire safety) | abnt.org.br |

## Key Laws and Regulations

### Lei 14.133/2021 — Nova Lei de Licitacoes

The new public procurement law fundamentally reshapes how construction companies interact with the government:

| Aspect | Requirement | AI Ventures Relevance |
|--------|------------|----------------------|
| **Electronic licitacoes** | All public procurement must use electronic platforms (PNCP) | Creates structured, machine-readable data for our licitacao monitoring agent |
| **PNCP publication** | All editais, contracts, and outcomes published on Portal Nacional de Contratacoes Publicas | Single national data source for monitoring all 5,570 municipalities |
| **SINAPI/SICRO mandatory** | Reference cost systems mandatory for public works budgets | Our cost intelligence tools validate against these benchmarks |
| **BDI regulation** | Detailed BDI (Bonificacao e Despesas Indiretas) breakdown required | LLM-powered BDI analysis and calculation tools |
| **Seguro garantia** | Performance bonds up to 30% of contract value (Art. 96-101) | Cross-vertical with insurance-surety |
| **Dialogo competitivo** | New procurement modality for complex/innovative projects | Opportunity for AI Ventures to participate as technical consultants |

### Decreto 10.306/2020 — BIM Mandate

| Phase | Timeline | Requirement |
|-------|----------|-------------|
| Phase 1 | January 2021 | BIM required for architecture and engineering in new federal projects above R$10M |
| Phase 2 | January 2024 | BIM extended to project execution/construction phases |
| Phase 3 | January 2028 | Full lifecycle BIM (design, construction, operations, maintenance) |

**Impact on mid-market**: Most mid-market firms are still in early Phase 1 adoption. Firms that want to compete for federal contracts (especially PAC infrastructure) must build BIM capabilities. AI Ventures' BIM Data Integration project bridges the gap between BIM models and financial/ERP systems.

### SINAPI — Sistema Nacional de Pesquisa de Custos e Indices da Construcao Civil

| Aspect | Detail |
|--------|--------|
| **Mandatory for** | All construction projects funded by Caixa Economica Federal (including MCMV) |
| **Coverage** | 100,000+ cost compositions covering labor, materials, equipment |
| **Update frequency** | Monthly, with annual rebase |
| **Regional variation** | Costs adjusted by state (27 UFs) with differentiation for capital vs. interior |
| **Compliance check** | Project budgets audited against SINAPI references; overpricing flagged as irregularity |
| **Data access** | Available via Caixa website; structured data for automated ingestion |

### SICRO — Sistema de Custos Referenciais de Obras

| Aspect | Detail |
|--------|--------|
| **Mandatory for** | DNIT infrastructure projects (roads, bridges, railways) |
| **Coverage** | Infrastructure-specific compositions (earthwork, paving, drainage, bridges) |
| **Update frequency** | Periodic, managed by DNIT |
| **Complementary to** | SINAPI — SICRO covers infrastructure items not in SINAPI |

### CUB — Custo Unitario Basico

| Aspect | Detail |
|--------|--------|
| **Published by** | Sinduscon (state chapters), mandated by Lei 4.591/1964 |
| **Purpose** | Monthly reference cost per m2 of construction by project type and state |
| **Used for** | Contract price indexation, incorporation cost estimates, judicial construction valuations |
| **Variants** | Residential (R1, R8, R16), commercial (CSL, CAL), industrial (GI), by number of floors and standard |

### NR-18 — Condicoes de Seguranca e Saude no Trabalho na Industria da Construcao

| Aspect | Detail |
|--------|--------|
| **Scope** | All construction sites in Brazil |
| **Key requirements** | Safety planning (PCMAT/PGR), fall protection, scaffolding, electrical safety, equipment |
| **Enforcement** | MTE auditors; fines range from R$2K to R$200K+ per infraction |
| **Documentation** | Detailed safety records required; our Compliance Tracker automates documentation |
| **Recent update** | 2020 revision modernized requirements, added risk management approach |

### Environmental Licensing

| License Type | When Required | Issuing Body |
|-------------|--------------|-------------|
| **LP** (Licenca Previa) | Before project design, for environmental viability assessment | IBAMA (federal) or state environmental agency |
| **LI** (Licenca de Instalacao) | Before construction begins | State environmental agency |
| **LO** (Licenca de Operacao) | Before building occupation/operation | State/municipal environmental agency |
| **Dispensa** | Small projects below impact thresholds | Municipal authority |

### LGPD Considerations

Construction companies handling personal data (employee records, resident data for condominios, subcontractor information) must comply with LGPD. Key areas:

- **Employee data**: Biometric access control, safety records, medical exams (ASO)
- **Resident data** (condominios): Personal information, financial records, communication logs
- **Subcontractor data**: Registration, financial, and compliance documentation
- **Video surveillance**: Construction site cameras capturing worker/visitor images

## Compliance Automation Opportunities

| Regulation | Current Process | AI Solution | Project Link |
|-----------|----------------|-------------|-------------|
| SINAPI compliance | Manual lookup and comparison per budget line item | Automated SINAPI matching and variance detection | Cost Control Dashboard |
| NR-18 documentation | Paper forms, manual filing | Digital checklists, photo AI, automated reports | Compliance Tracker |
| Environmental permits | Spreadsheet tracking of license expiration dates | Automated monitoring, renewal alerting, document management | Compliance Tracker |
| BIM requirements | Manual BIM model creation disconnected from cost/schedule data | BIM-ERP integration, automated quantity extraction | BIM Data Integration |
| Lei 14.133 procurement | Manual edital reading across multiple platforms | NLP extraction, automated matching, BDI analysis | Public Works Intelligence Radar |

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
