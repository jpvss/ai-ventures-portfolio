---
title: "Auction Market — Regulatory Map"
type: regulatory-map
vertical: auctions
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: monthly
tags: [auctions, regulatory, compliance, brazil, CPC, alienacao-fiduciaria]
---

# Auction Market — Regulatory Map

## Regulatory Bodies

| Agency | Jurisdiction | Key Role |
|--------|-------------|----------|
| **Poder Judiciario (TJs)** | State-level judicial auctions | Conducts judicial auctions per CPC/2015; 27 separate TJ systems |
| **CNJ (Conselho Nacional de Justica)** | National judiciary oversight | Sets rules for electronic auctions (Resolucao 236/2016) |
| **Receita Federal** | Federal tax authority | e-CAC portal, SLE system; tax implications for buyers |
| **Municipios** | Local government | ITBI collection on property transfers |
| **Cartorios de Registro de Imoveis** | Property registration | Matricula management, encumbrance records |

## Key Legislation

| Law/Regulation | Date | Summary | Impact on Clients |
|---------------|------|---------|-------------------|
| **CPC/2015 Arts. 879-903** | 2015 | Judicial auction rules: edital requirements, preco vil prohibition, 25% down + 30 installment payment option | AI recommendations must comply with minimum price rules; edital parsing must extract all CPC-mandated fields |
| **Lei 9.514/1997** | 1997 | Alienacao fiduciaria framework; two-auction system; debtor notification requirements; 30-day auction deadline | Extrajudicial pipeline must track notification compliance; two-auction pricing logic must be modeled |
| **Lei 14.133/2021** | 2021 | Nova Lei de Licitacoes for government asset disposal | Government auction platform integration compliance required |
| **CNJ Resolucao 236/2016** | 2016 | Electronic auction regulation: leiloeiro credenciamento (min. 3 years experience), 5% commission, 5-day minimum pre-lance period, 3-minute extension rule | Platform design must comply with timing rules; commission calculations must follow 5% standard |
| **Lei 14.711/2023** | 2023 | Updates to alienacao fiduciaria procedures | Integration updates needed for extrajudicial auction tracking |
| **LGPD** | 2018 (effective 2020) | Data protection for scraped/aggregated data, investor data handling, debtor data protection | Scraping must respect personal data; debtor names may be PII; investor profiles need consent management |

## Compliance Requirements

### Judicial Auctions (CPC/2015 Arts. 879-903)

Key requirements that affect AI systems:

- **Edital requirements**: Must contain all property details, encumbrances, and conditions — AI edital parsers must extract all mandated fields
- **Preco vil prohibition**: Properties cannot be sold below the legally defined minimum — AI pricing recommendations must enforce this floor
- **Payment terms**: 25% down payment + up to 30 monthly installments — investment calculators must model these cash flows
- **Auction timing**: Specific rules on lance periods, extensions, and notification deadlines

### Extrajudicial Auctions (Lei 9.514/1997)

- **Two-auction system**: First auction at appraised value, second auction at outstanding debt — AVM models must account for both price floors
- **Debtor notification**: Mandatory notification procedures before auction — tracking systems must verify compliance
- **30-day deadline**: Auctions must occur within specified timeframes

### Electronic Auction Rules (CNJ Resolucao 236/2016)

- **Leiloeiro credenciamento**: Minimum 3 years of experience required
- **Commission**: 5% standard (paid by buyer)
- **Pre-lance period**: Minimum 5 days before auction
- **Extension rule**: 3-minute extension after each lance — platform integrations must respect timing
- **Electronic signature**: Required for digital auction processes

### Data Protection (LGPD)

Specific LGPD implications for the auction vertical:

- **Scraped data**: Aggregating data from 1,000+ leiloeiro websites raises LGPD concerns when personal data (debtor names, addresses) is collected
- **Debtor data protection**: Debtor names and financial information appearing in editais may constitute PII requiring careful handling
- **Investor data**: Profiles, investment preferences, and financial data require explicit consent and purpose limitation
- **Data minimization**: Scraping systems should collect only necessary data, avoiding excessive personal information
- **Right to erasure**: Systems must support deletion requests from data subjects

### Tax Implications for Buyers

| Tax/Fee | Details |
|---------|---------|
| **ITBI** | Typically 2-3% of arrematacao value; varies by municipality; due at property transfer |
| **IR sobre ganho de capital** | 15-22.5% on capital gain at resale; progressive rates apply |
| **Leiloeiro commission** | Typically 5% per CNJ Resolucao 236; paid by buyer |
| **IPTU liability** | Potential liability for outstanding IPTU debts depending on auction type and edital terms |
| **Condominio liability** | Potential liability for outstanding condominio debts depending on auction type and edital terms |

## Compliance Calendar

| Event | Obligation | Notes |
|-------|-----------|-------|
| Pre-auction (5+ days) | Edital publication and pre-lance period | CNJ Resolucao 236 mandates minimum 5-day pre-lance |
| At auction | Preco vil enforcement | CPC/2015 minimum price rules |
| Post-arrematacao | ITBI payment | Municipal deadline varies |
| Post-arrematacao | Matricula transfer registration | Cartorio processing |
| On resale | IR capital gain declaration | Annual IR filing cycle |

## Automation Opportunities

| Process | Current State | Automation Potential | Estimated Savings |
|---------|--------------|---------------------|-------------------|
| Edital analysis | Manual lawyer review, R$2,000/property | NLP parsing + risk scoring | R$1,950/property (R$2,000 to R$50) |
| Matricula encumbrance check | Manual cartorio visits | OCR + structured extraction | Hours to minutes per property |
| CPC/Lei 9.514 compliance check | Manual legal review | Rules engine against parsed edital | Automated flagging of non-compliant auctions |
| ITBI calculation | Manual per-municipality lookup | Database of municipal rates + auto-calc | Integrated into investment scoring |
| Post-arrematacao deadline tracking | Spreadsheet/manual | Automated workflow with alerts | Prevents missed deadlines, reduces registration time |

## Recent Changes

- **Lei 14.711/2023**: Updated alienacao fiduciaria procedures, requiring integration updates for extrajudicial auction tracking systems
- **Continued growth in electronic auctions**: CNJ Resolucao 236/2016 framework increasingly adopted as courts modernize
- **Nova Lei de Licitacoes (Lei 14.133/2021)**: Full implementation affecting government asset disposal auctions

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-05-02*
