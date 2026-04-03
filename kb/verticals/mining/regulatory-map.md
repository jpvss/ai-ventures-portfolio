---
title: "Mining Consulting — Regulatory Map"
type: regulatory-map
vertical: mining
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: monthly
tags: [mining, regulatory, compliance, ANM, IBAMA, CFEM, dam-safety, NR-22]
---

# Mining Consulting — Regulatory Map

## Regulatory Bodies

| Agency | Jurisdiction | Key Role | Digital Systems |
|--------|-------------|----------|-----------------|
| **ANM** (Agencia Nacional de Mineracao) | Federal | Mining rights, royalties, dam safety | PGRM (March 2025, built by Serpro), SIGMINE Portal, Cadastro Mineiro, DIEF-CFEM |
| **IBAMA** | Federal | Environmental licensing (federal-scope projects) | Portal Ecossistemas |
| **SEMAD/COPAM** (Minas Gerais) | State | State environmental licensing | SLA system (since 2019) |

## Key Legislation

| Law/Regulation | Date | Summary | Impact on Clients |
|---------------|------|---------|-------------------|
| **Lei 13.540/2017** | 2017 | CFEM reform -- changed calculation basis to receita bruta minus taxes (ICMS/PIS/COFINS) with substance-specific aliquots of 1%--3.5% | Requires precise monthly CFEM calculation; errors lead to 30% surcharge penalties on underpayments |
| **Lei 14.066/2020** | 2020 | Dam safety (PNSB) -- mandates PAE for ALL mining tailings dams | PAE mandatory, stability declarations required, real-time data submission to ANM, personal criminal liability for executives, integrates with SNISB |
| **NR-22** | Updated May 2024 | Mining safety and health regulations | PGR mandatory, CIPAMIN committees, SIPATMIN events, training requirements, incident reporting; mostly manual compliance currently |
| **Lei 9.605/98** | 1998 | Environmental crimes law | Fines from R$50 to R$50M for environmental violations |

## Compliance Requirements

### Mandatory Reporting

| Report | Agency | Frequency | Penalty for Non-Compliance |
|--------|--------|-----------|---------------------------|
| **CFEM** (Compensacao Financeira pela Exploracao de Recursos Minerais) | ANM | Monthly payment | 30% surcharge on underpayments; overpayments result in lost revenue (R$560K--R$1.4M/year typical) |
| **DIEF** (Declaracao de Informacoes Economico-Fiscais) | ANM | Monthly (via PGRM platform) | Fines and potential mining rights suspension |
| **RAL** (Relatorio Anual de Lavra) | ANM | Annual | Mining rights suspension |
| **DIPEM** | ANM | Periodic | Regulatory penalties |
| **Environmental monitoring reports** | IBAMA / SEMAD | Per license conditions | License suspension (operational halt: R$500K--R$5M/day) |
| **Dam stability declarations** | ANM | Per Lei 14.066/2020 | Criminal liability for executives, operational shutdown |
| **NR-22 PGR** | Ministry of Labor | Continuous maintenance | Labor fines, operational shutdown |
| **CIPAMIN records** | Ministry of Labor | Meeting records | Labor compliance penalties |
| **Incident reports** | ANM / Labor | Per occurrence | Fines, criminal liability |

### CFEM Aliquot Schedule (Lei 13.540/2017)

| Substance | Aliquot |
|-----------|---------|
| Iron ore | 3.5% |
| Bauxite, manganese, niobium | 3.0% |
| Gold | 1.5% |
| Diamonds | 2.0% |
| Other metallic minerals | 2.0% |
| Construction materials | 1.0% |
| Fertilizers | 0.2% |

**Calculation basis**: Receita bruta minus ICMS, PIS, and COFINS deductions.

### Environmental Licensing (LP/LI/LO)

Three-phase licensing system:
- **LP** (Licenca Previa): Preliminary environmental approval
- **LI** (Licenca de Instalacao): Construction/installation authorization
- **LO** (Licenca de Operacao): Operational permit

Each license contains **condicionantes** (conditions) with specific deadlines. Missing a single condicionante can trigger license suspension. Most mid-market miners track these in Excel.

**Minas Gerais specifics (SEMAD/COPAM)**:
- SLA system operational since 2019
- AAF (Autorizacao Ambiental de Funcionamento) for classes 1--2 activities
- Regular monitoring report submissions required

### Dam Safety (Lei 14.066/2020)

Post-Brumadinho legislation applies to ALL mining tailings dams:
- PAE (Plano de Acao de Emergencia) mandatory
- Stability declarations required
- Real-time instrumentation data submission to ANM
- Integration with SNISB (Sistema Nacional de Informacoes sobre Seguranca de Barragens)
- **Personal criminal liability for executives** for non-compliance
- Instrumentation includes piezometers, inclinometers with anomaly detection requirements

### NR-22 Safety and Health (Updated May 2024)

- PGR (Programa de Gerenciamento de Riscos) mandatory
- CIPAMIN (mining safety committee) with documented records
- SIPATMIN (safety awareness events) required
- Training requirements with completion tracking
- Incident and near-miss reporting

## Compliance Calendar

| Period | Obligation | Agency | Notes |
|--------|-----------|--------|-------|
| Monthly | CFEM payment | ANM | Via PGRM platform (March 2025+) |
| Monthly | DIEF submission | ANM | Digital submission via PGRM |
| Annual | RAL submission | ANM | Auto-generation possible from production/geological/sales data |
| Ongoing | Dam stability declarations | ANM | Real-time data to SNISB |
| Per license schedule | Environmental condicionante reports | IBAMA/SEMAD | LP/LI/LO conditions with specific deadlines |
| Per license schedule | PRAD milestone reports | IBAMA/SEMAD | Mine rehabilitation progress |
| Ongoing | Water monitoring (outorga) | ANA/State agencies | Flow rates, quality parameters |
| Per occurrence | Incident reporting | ANM/Labor | Safety incidents and near-misses |
| Continuous | PGR maintenance | Labor | NR-22 compliance |
| Periodic | CIPAMIN meetings and records | Labor | NR-22 compliance |

## Automation Opportunities

| Process | Current State | Automation Potential | Estimated Savings |
|---------|--------------|---------------------|-------------------|
| CFEM calculation | Excel spreadsheets | Full automation via NF-e data extraction + aliquot logic | 40--80 hours/month, R$560K--R$1.4M/year in error recovery |
| DIEF submission | Manual data entry | Auto-populated from ERP/production data via PGRM API | 20--40 hours/month |
| RAL preparation | Manual compilation | Auto-generated from production, geological, and sales databases | 200+ hours/year |
| Environmental condicionante tracking | Excel/manual | Automated calendar + alerts + evidence packages | Prevention of R$500K--R$5M/day shutdowns |
| Dam safety monitoring | Semi-manual | Real-time sensor data aggregation + anomaly detection | Compliance assurance, criminal liability protection |
| NR-22 PGR management | Paper/spreadsheet | Digital incident tracking, training management, CIPAMIN records | 10--20 hours/month, audit readiness |

## Recent Changes

- **March 2025**: ANM launched PGRM platform (built by Serpro) for digital CFEM/DIEF submission, making digital compliance effectively mandatory
- **May 2024**: NR-22 updated with new safety and health requirements
- **Ongoing**: SNISB integration requirements expanding for dam safety monitoring

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-05-02*
