---
title: "Energy & Infrastructure — Regulatory Map"
type: regulatory-map
vertical: energy-infrastructure
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: monthly
tags: [energy-infrastructure, regulatory, ANEEL, CCEE, ONS, Marco-Legal-GD, Lei-14300]
---

# Energy & Infrastructure — Regulatory Map

## Regulatory Bodies

| Agency | Jurisdiction | Key Role | Digital Systems |
|--------|-------------|----------|-----------------|
| **ANEEL** (Agencia Nacional de Energia Eletrica) | Federal | Electricity regulation, tariffs, GD rules, licensing | SIGEL, SIGA, Audiencias Publicas portal, Normative portal |
| **ONS** (Operador Nacional do Sistema Eletrico) | Federal | Grid operation, dispatch, system balance | ONS Data portal, PEN (Plano de Expansao) |
| **CCEE** (Camara de Comercializacao de Energia Eletrica) | Federal | Energy trading settlement, Mercado Livre administration | CLIQ (trading platform), InfoMercado, SCDE |
| **EPE** (Empresa de Pesquisa Energetica) | Federal | Energy planning, demand forecasting, atlas resources | Atlas Solar, PDE (Plano Decenal de Energia) |
| **MME** (Ministerio de Minas e Energia) | Federal | Energy policy, concessions, strategic planning | SIMP, regulatory portals |
| **INMET** (Instituto Nacional de Meteorologia) | Federal | Weather and irradiation data | INMET API, BDMEP database |
| **Distribuidoras** (CEMIG, Enel, CPFL, Energisa, Equatorial, Neoenergia) | Regional | Energy distribution, GD connection, billing, compensation | Individual portals for UC management and compensation reports |

## Key Legislation

| Law/Regulation | Date | Summary | Impact on Clients |
|---------------|------|---------|-------------------|
| **REN 482/2012** | 2012 | Original GD framework -- established net metering (sistema de compensacao) for micro/mini generation | Created the GD market; full compensation of injected energy against consumption |
| **REN 687/2015** | 2015 | Expanded GD -- introduced remote generation (GD remota), condominios, and consortia models | Enabled GD business models beyond on-site; allowed multiple UCs per plant |
| **Lei 14.300/2022** (Marco Legal da GD) | January 2022 | Legal framework for GD -- codified compensation rights, introduced fio B tariff transition, set transition rules | Plants connected before 07/01/2023 grandfathered under old rules until 2045; new plants face progressive TUSD Fio B charges |
| **REN 1.000/2021** | 2021 | Consolidated GD procedures -- access rules, connection standards, metering | Standardized connection process across distribuidoras; defines technical requirements |
| **REN 1.059/2023** | 2023 | Updated GD compensation framework -- implements Lei 14.300 details | Defines fio B transition timeline, compensation calculation methodology, new plant categories |
| **REN 1.098/2023** | 2023 | Mercado Livre rules update -- reduced eligibility threshold | Progressive opening of free market to smaller consumers |
| **LGPD** (Lei 13.709/2018) | 2020 (enforcement) | Data protection for energy consumer data | Consumer consent required for UC data processing; distribuidora data sharing restrictions |

## Compensation Rules (Sistema de Compensacao)

### Pre-Marco Legal (plants connected before 07/01/2023)
- Full compensation: 100% of injected kWh offsets consumed kWh (net metering)
- Credits valid for 60 months
- Grandfathered under old rules until 2045
- No TUSD Fio B charge on compensated energy

### Post-Marco Legal (plants connected after 07/01/2023)
- Progressive introduction of TUSD Fio B (wire cost):
  - 2023: 15% of TUSD Fio B
  - 2024: 30% of TUSD Fio B
  - 2025: 45% of TUSD Fio B
  - 2026: 60% of TUSD Fio B
  - 2027: 75% of TUSD Fio B
  - 2028+: 90% of TUSD Fio B
- Credits still valid for 60 months
- TE (Tarifa de Energia) still fully compensated

### Billing Complexity Implications
- Each UC must be calculated based on connection date (pre vs. post Marco Legal)
- Different fio B percentages apply per year for post-2023 plants
- Distribuidoras apply different tariff structures (horo-sazonal vs. convencional)
- GD remota adds cross-UC credit allocation complexity
- Mixed portfolios (pre and post Marco Legal plants) require dual calculation logic

## LGPD for Energy Consumer Data

- **Consumer consent**: Required for processing UC holder data (CPF/CNPJ, consumption history, address)
- **Data sharing**: Distribuidora data sharing with third parties requires consumer authorization
- **Data retention**: Energy consumption data retention subject to LGPD time limits unless regulatory obligation applies
- **Impact on GD gestoras**: Must maintain consent records for all UCs in portfolio; affects prospecting data collection

## Compliance Calendar

| Period | Obligation | Agency | Notes |
|--------|-----------|--------|-------|
| Monthly | Fatura reconciliation per UC | Distribuidora | Compensation credits applied; discrepancies must be disputed within billing cycle |
| Monthly | CCEE settlement (comercializadoras) | CCEE | Trading settlement via CLIQ; financial exposure for imbalances |
| Annual | ANEEL annual information report | ANEEL | Generation data, plant status, UC portfolio updates |
| Per connection | Access request and connection approval | Distribuidora | REN 1.000/2021 procedures; parecer de acesso within 15--30 days |
| Ongoing | UC portfolio management | Distribuidora | Add/remove UCs from compensation group; allocation percentage updates |
| Per regulatory change | System/process updates | ANEEL | Tariff revisions, compensation rule changes, new RENs |

## Automation Opportunities

| Process | Current State | Automation Potential | Estimated Savings |
|---------|--------------|---------------------|-------------------|
| Fatura reconciliation | Manual PDF parsing, Excel comparison | Full automation via fatura parser + UC database | 40--80 hours/month for 100+ UC portfolio |
| Compensation calculation | Manual per-UC calculation with distribuidora rules | Auto-calculation with pre/post Marco Legal logic | R$50K--R$200K/yr in recovered billing errors |
| CCEE settlement reconciliation | Manual comparison of metered vs. settled volumes | Automated reconciliation with SCDE data | 20--40 hours/month for active traders |
| Regulatory change monitoring | Manual reading of ANEEL diario oficial | RAG-based monitoring with impact assessment | Proactive compliance; avoid missed changes |
| UC portfolio management | Manual distribuidora portal interactions | Semi-automated via portal scraping/API | 10--20 hours/month |

## Recent Changes

- **2023**: Lei 14.300/2022 fully in effect; fio B transition begins for new plants
- **2023**: ANEEL REN 1.059/2023 details compensation methodology for Marco Legal transition
- **2024--2025**: Progressive fio B percentage increase (30% in 2024, 45% in 2025)
- **2025**: Mercado Livre eligibility threshold continuing progressive reduction
- **Ongoing**: Distribuidoras digitizing compensation portals -- CEMIG, Enel, CPFL offering API/portal access

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-05-02*
