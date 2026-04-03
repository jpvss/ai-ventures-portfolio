---
title: "Automotive — Regulatory Map"
type: regulatory-map
vertical: automotive
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: monthly
tags: [automotive, regulatory, compliance, DENATRAN, DETRAN, CTB, CONTRAN]
---

# Automotive — Regulatory Map

## Regulatory Bodies

| Agency | Jurisdiction | Key Role | Website |
|--------|-------------|----------|---------|
| **DENATRAN** (Departamento Nacional de Trânsito) | National vehicle registration | Maintains RENAVAM (national vehicle registry), vehicle identification standards, recall tracking | gov.br/denatran |
| **SENATRAN** (Secretaria Nacional de Trânsito) | National traffic policy | Sets national traffic policy; DENATRAN operates under SENATRAN since 2021 restructuring | gov.br/senatran |
| **DETRAN** (Departamento Estadual de Trânsito) | State-level vehicle registration | 27 state DETRANs handle licensing (CRLV), transfers, inspections, IPVA collection | Varies by state |
| **CONTRAN** (Conselho Nacional de Trânsito) | National traffic regulation | Issues resolutions on vehicle standards, safety, recalls, identification | gov.br/contran |
| **PROCON** | Consumer protection | Enforces CDC (Código de Defesa do Consumidor) in vehicle transactions | State-level |
| **IBAMA** | Environmental compliance | Vehicle emissions standards, CONAMA resolutions | ibama.gov.br |
| **Banco Central** | Financial regulation | Regulates vehicle-backed credit (CDC, consórcio, refinancing) | bcb.gov.br |

## Key Legislation

| Law/Regulation | Date | Summary | Impact on Clients |
|---------------|------|---------|-------------------|
| **CTB** (Código de Trânsito Brasileiro — Lei 9.503/1997) | 1997 (amended) | Comprehensive traffic code governing vehicle registration, transfer, licensing, inspections | Defines all vehicle transfer procedures; arts. 123–134 cover registration and transfer |
| **CONTRAN Resolução 886/2021** | 2021 | Vehicle identification standards — VIN, chassi marking, engine number rules | Chassi/VIN validation critical for fraud detection in valuations |
| **CDC** (Código de Defesa do Consumidor — Lei 8.078/1990) | 1990 | Consumer protection code | Art. 26: 90-day warranty on used vehicles from dealers; Art. 35: advertising obligations |
| **LGPD** (Lei 13.709/2018) | 2020 (enforcement) | General Data Protection Law | Consent required for processing vehicle owner personal data; up to 2% revenue / R$50M per infraction |
| **Lei 14.010/2020** | 2020 | Digital vehicle transfer provisions | Enables digital CRV transfer process — reduced friction in vehicle transactions |
| **CONTRAN Resolução 819/2021** | 2021 | Digital CRLV (Certificado de Registro e Licenciamento de Veículo) | Mandatory digital CRLV replaces paper; enables digital verification workflows |
| **Lei 6.729/1979** (Lei Ferrari) | 1979 (amended) | Regulates relationship between automakers and authorized dealers | Protects authorized dealer networks; does not apply to multimarca/used dealers |
| **Portaria DENATRAN 1.457/2019** | 2019 | Recall tracking and notification requirements | Dealers must check recall status before transfer; data available via DENATRAN API |

## Vehicle Transfer Process

The transfer of a used vehicle in Brazil involves multiple regulatory touchpoints:

1. **Seller provides**: CRV (Certificado de Registro do Veículo) with signed transfer authorization
2. **Buyer performs**:
   - Verify vehicle status via DETRAN (débitos, multas, IPVA, DPVAT/Seguro Obrigatório)
   - Verify no judicial restrictions (bloqueios judiciais)
   - Verify recall compliance (DENATRAN database)
   - Vehicle inspection (vistoria) at DETRAN-authorized facility
   - Pay transfer tax (ITCMD varies by state, typically 1–4% of FIPE value)
   - Register transfer at DETRAN within 30 days (Art. 123 CTB)
3. **DETRAN issues**: New CRLV in buyer's name

**Key automation opportunities**: Steps 2a–2d (verification) can be automated via DENATRAN/DETRAN API integrations, reducing transfer preparation from hours to minutes.

## Compliance Requirements

### Vehicle Valuation and Advertising

**CDC obligations for dealers**:
- Art. 26: Used vehicles sold by dealers carry a **90-day warranty** (vícios ocultos)
- Art. 31: All advertising must include clear, accurate information about vehicle condition, year, mileage
- Art. 35: Dealer is bound by advertised terms and prices
- Art. 37: Misleading or abusive advertising is prohibited — AI-generated listings must be factually accurate

**FIPE as legal reference**:
- FIPE is used as the legal reference price by courts, insurers, and tax authorities
- IPVA (Imposto sobre a Propriedade de Veículos Automotores) is calculated based on FIPE value
- Insurance indemnities (perda total / sinistro) reference FIPE
- Vehicle-backed loan LTV calculations use FIPE as collateral floor

### Data Protection (LGPD)

- **Vehicle owner data**: Name, CPF, address, phone collected during valuation/lead capture requires consent
- **Vehicle data**: Placa, chassi, RENAVAM are linked to owner identity — qualify as personal data in many interpretations
- **deixacomigo implications**: Lead capture form requires explicit consent statement; data stored in Supabase must have retention policy
- **Marketplace scraping**: Public listing data generally permissible, but aggregation with personal data requires LGPD compliance
- **Up to 2% of revenue or R$50M per infraction** for violations

### Financial Regulation (Vehicle-Backed Credit)

- **Banco Central Resolução 4.893/2021**: Regulates vehicle-backed credit operations (CDC auto, refinancing)
- **Collateral valuation**: Financial institutions must have documented methodology for vehicle collateral valuation — FIPE alone increasingly questioned by regulators
- **Alienação fiduciária**: Vehicle lien registration at DETRAN required; AI systems must check for existing liens during valuation
- **Consórcio**: Regulated by Banco Central; vehicle collateral rules apply differently

## Compliance Calendar

| Period | Obligation | Agency | Penalty for Non-Compliance |
|--------|-----------|--------|---------------------------|
| Annual | IPVA payment (based on FIPE value) | State DETRAN/Secretaria da Fazenda | Vehicle seized; cannot transfer |
| Annual | CRLV renewal (licensing) | DETRAN | Vehicle seized; fine |
| Within 30 days | Transfer registration after sale | DETRAN (Art. 123 CTB) | Fine of R$293.47 + daily penalty |
| Continuous | Recall compliance check before transfer | DENATRAN (Portaria 1.457/2019) | Transfer may be blocked |
| Continuous | LGPD consent for customer data | ANPD | Up to 2% revenue / R$50M |
| Continuous | CDC warranty obligations (90 days) | PROCON | Fines, mandatory repair/refund |
| Ongoing | Vehicle inspection (vistoria) for transfer | DETRAN | Transfer blocked |

## Automation Opportunities

| Process | Current State | Automated State | Estimated Savings |
|---------|--------------|----------------|-------------------|
| Vehicle status verification (débitos, multas, restrições) | Manual DETRAN website lookups, 15–30 min/vehicle | API integration with DETRAN systems, instant verification | 90% time reduction per vehicle |
| Recall status check | Manual DENATRAN portal lookup | Automated batch check against DENATRAN recall database | Prevents transfer of recalled vehicles; reduces liability |
| CRLV/CRV document verification | Manual visual inspection | OCR + AI document verification for authenticity, data extraction | Reduces fraud; 10x faster |
| Transfer tax calculation | Manual FIPE lookup + state tax rate application | Automated FIPE pull + state-specific tax rules engine | Eliminates calculation errors; instant buyer cost estimate |
| Lien/restriction check (alienação fiduciária) | Manual DETRAN system lookup | Automated check via DETRAN API integration | Prevents acquisition of encumbered vehicles |
| Vehicle history compilation | Multiple manual system lookups (DENATRAN, DETRAN, recalls, accidents) | Aggregated vehicle history report from all sources in one API call | Comprehensive report in seconds vs. hours |

## State-Level Variation

A critical complexity in Brazilian automotive regulation is that each of the 27 states operates its own DETRAN with varying:
- **IPVA rates**: Range from 1% to 4% of FIPE value depending on state and vehicle age
- **Transfer fees**: Vary by state (R$100–R$500+)
- **Inspection (vistoria) requirements**: Different criteria and authorized inspection networks
- **Digital readiness**: Some DETRANs offer APIs (SP, RJ); others are manual-only
- **Tax incentives**: Some states exempt EVs or older vehicles from IPVA

**Implication for AI Ventures**: Solutions must be state-aware. Pricing engines must factor in state-specific costs (IPVA, transfer fees) when calculating total cost of ownership for buyers.

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-05-02*
