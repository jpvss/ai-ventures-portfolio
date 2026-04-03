---
title: "Real Estate — Regulatory Map"
type: regulatory-map
vertical: real-estate
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: monthly
tags: [real-estate, regulatory, compliance, incorporacao, LGPD, cartorio, SREI]
---

# Real Estate — Regulatory Map

## Regulatory Bodies

| Agency/Entity | Jurisdiction | Key Role | Digital Systems |
|---------------|-------------|----------|-----------------|
| **Prefeituras municipais** | Municipal | Zoning (Plano Diretor), building permits (alvara), Habite-se, ITBI collection | GeoSampa (SP), BHMap (BH), SIGEO (RJ), varies by municipality |
| **Cartorios de Registro de Imoveis (RI)** | State/Federal | Property registration, matricula, averbacao, SREI digital registry | SREI (Lei 14.382/2022), ARISP (SP), ONR (national) |
| **CVM** (Comissao de Valores Mobiliarios) | Federal | FII regulation, real estate securities (CRI, LCI) | CVM Portal, ICVM 472/2008 (FII rules) |
| **CAIXA Economica Federal** | Federal | MCMV program, SBPE financing, FGTS credit lines | CAIXA Habitacao portal, SIOPI |
| **Banco Central (BACEN)** | Federal | Real estate credit regulation, macroprudential rules | SFH/SFI framework |
| **Receita Federal** | Federal | RET (Regime Especial de Tributacao) for incorporacoes, SPE taxation | e-CAC, SPED fiscal |
| **SECOVI/CBIC** | Industry | Industry standards, market data, advocacy | Surveys, market reports |

## Key Legislation

| Law/Regulation | Date | Summary | Impact on Clients |
|---------------|------|---------|-------------------|
| **Lei 4.591/1964** | 1964 | Law of Incorporacoes -- governs real estate development, memorial de incorporacao, buyer rights | Core framework for all incorporation activity; memorial de incorporacao required before sales |
| **Lei 10.931/2004** | 2004 | Patrimonio de afetacao -- allows SPE asset segregation for buyer protection | Each SPE's assets/liabilities must be segregated; requires per-entity accounting; enables RET tax regime |
| **Lei 13.786/2018** (Lei do Distrato) | 2018 | Regulates contract cancellation in incorporacoes | Buyer can retain only 25--50% of paid amounts on distrato; incorporadoras must provision for distrato risk |
| **Lei 14.382/2022** (SREI) | 2022 | Sistema de Registro Eletronico de Imoveis -- digital cartorio | Electronic matricula, digital averbacao, ONR national platform; creates machine-readable property data |
| **Lei 14.133/2021** | 2021 | New public procurement law -- affects public land sales and PPPs | Public land auctions follow new procurement rules; impacts land acquisition from government |
| **Lei 8.009/1990** | 1990 | Bem de familia -- protects primary residence from seizure | Limits enforcement on auction properties that are primary residences; critical for leilao legal analysis |
| **Lei 9.514/1997** | 1997 | Alienacao fiduciaria -- fiduciary alienation of real property | Enables extrajudicial foreclosure (leilao extrajudicial); Art. 27 governs auction procedures |
| **CPC Art. 879--903** | 2015 | Judicial auction (hasta publica) procedures | Governs judicial leilao process, penhora, avaliacao, arrematacao |
| **ICVM 472/2008** (updated) | 2008+ | FII regulation -- governance, reporting, distribution rules | Mandates quarterly reporting, NAV calculation, tenant disclosure for FII managers |

## LGPD Implications for Property Data

Property transactions involve extensive personal data subject to LGPD (Lei 13.709/2018):

| Data Category | LGPD Basis | Risk Level | Mitigation |
|---------------|-----------|------------|------------|
| Buyer CPF, income, employment | Consent + contract execution (Art. 7, II/V) | High | Explicit consent forms; data minimization; encrypted storage |
| ITBI transaction records | Legitimate interest (Art. 7, IX) | Medium | Anonymization for analytics; no individual-level exposure in dashboards |
| Matricula ownership history | Public registry (Art. 7, X) | Low | Public data, but aggregation requires care |
| Property photos/location | Legitimate interest | Medium | Remove personal identifiers; geo-fence sensitive areas |
| Leilao debtor information | Legal obligation (Art. 7, II) | High | Process only within auction context; strict access controls |

**Key LGPD obligations for real estate AI systems:**
- Data Protection Impact Assessment (DPIA/RIPD) required for large-scale property data processing
- Data Processing Officer (DPO/encarregado) designation
- Consent management for buyer/seller data
- Right to deletion conflicts with cartorio record obligations (legal basis exception)

## Compliance Calendar

| Period | Obligation | Entity | Notes |
|--------|-----------|--------|-------|
| Before sales launch | Memorial de incorporacao registration at cartorio RI | Incorporadora | Lei 4.591/1964 Art. 32; must include all 16 required documents |
| Monthly | SPE patrimonio de afetacao accounting | Incorporadora/SPE | Segregated financial statements per Lei 10.931/2004 |
| Monthly | RET tax payment (1--4% on gross revenue) | SPE | Regime Especial de Tributacao; replaces PIS/COFINS/IRPJ/CSLL |
| Quarterly | DIMOB (real estate transactions declaration) | Imobiliarias/Incorporadoras | Receita Federal; penalties for late/incorrect filing |
| Annual | IRPF reporting of property transactions | All parties | Buyer and seller tax obligations |
| Per transaction | ITBI payment | Buyer | Municipal tax, typically 2--3% of transaction value |
| Per project | Habite-se / auto de conclusao | Incorporadora | Municipal approval for occupancy |
| Per project | Averbacao de construcao | Incorporadora | Cartorio registration of completed construction |
| Ongoing | LGPD compliance for client data | All | DPO, consent management, DPIA |

## Recent Changes

- **2024--2025**: SREI (Lei 14.382/2022) rollout accelerating -- ARISP (SP) operational, ONR expanding nationally. Electronic matricula becoming standard in major cities.
- **2024**: MCMV Faixa 3 ceiling raised to R$350K; Faixa 4 (up to R$500K) under discussion. Subsidy structure updated.
- **2025**: CVM updating FII regulation (successor to ICVM 472) with enhanced ESG disclosure requirements.
- **2025**: Several municipalities launching digital ITBI platforms with API access (SP, BH, Curitiba leading).
- **2026**: ONR (Operador Nacional do Sistema de Registro Eletronico) targeting full national digital cartorio coverage.
- **Ongoing**: LGPD enforcement intensifying -- ANPD issuing sector-specific guidance for real estate data processing.

## Tax Structure for Incorporacoes

| Tax Regime | Applicable To | Rate | Notes |
|-----------|--------------|------|-------|
| **RET (Regime Especial de Tributacao)** | SPEs with patrimonio de afetacao | 1% (MCMV Faixa 1) / 4% (general) on gross revenue | Unifies PIS/COFINS/IRPJ/CSLL; requires patrimonio de afetacao |
| **Lucro Presumido** | Incorporadoras without RET | ~6.73% effective on gross revenue | Higher than RET; no patrimonio de afetacao required |
| **ITBI** | Per transaction | 2--3% of transaction/assessed value | Municipal tax; varies by city; often basis for AVM data |
| **IPTU** | Property holding | Varies by municipality | Progressive rates in some cities; exemptions for MCMV |

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-05-02*
