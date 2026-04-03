---
title: "Financial Services — Regulatory Map"
type: regulatory-map
vertical: financial-services
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [financial-services, regulation, BCB, LGPD, open-finance, SCR, compliance]
---

# Financial Services — Regulatory Map

## Regulatory Landscape Overview

Brazilian financial services is one of the most heavily regulated sectors, with the Banco Central do Brasil (BCB) and Conselho Monetário Nacional (CMN) as primary regulators. For mid-market fintechs, factorings, and FIDCs, the regulatory burden is disproportionate — they face the same requirements as large banks but without dedicated compliance teams.

## Primary Regulatory Bodies

| Regulator | Scope | Key Interactions | Impact on Mid-Market |
|-----------|-------|-----------------|---------------------|
| **BCB (Banco Central do Brasil)** | Banking regulation, monetary policy, payment systems, Open Finance | Licensing, SCR reporting, PIX regulation, Open Finance mandates | High — directly regulates SCDs, SEPs, payment institutions |
| **CMN (Conselho Monetário Nacional)** | Monetary and credit policy; sets high-level rules | Framework resolutions implemented by BCB | Medium — sets capital and operational requirements |
| **CVM (Comissão de Valores Mobiliários)** | Securities regulation; governs FIDCs and securitization | FIDC registration, reporting, investor protection | High for FIDCs — registration, disclosure, auditing requirements |
| **ANPD (Autoridade Nacional de Proteção de Dados)** | LGPD enforcement; data protection | Consent management, data processing legitimate interests, breach notification | Growing — ANPD ramping up enforcement; fines being applied |
| **COAF (Conselho de Controle de Atividades Financeiras)** | AML/CFT; anti-money laundering | Suspicious transaction reporting, KYC requirements | Medium — mandatory reporting for all financial institutions |
| **Receita Federal** | Tax administration; CNPJ registration | e-Financeira reporting, CNPJ validation, tax compliance | Medium — e-Financeira reporting requirements |

## Key Regulations

### Resolução 4.656/2018 — Fintech Regulation

**What it does**: Created two new institutional categories for fintechs:
- **SCD (Sociedade de Crédito Direto)**: Can originate credit using own capital only
- **SEP (Sociedade de Empréstimo entre Pessoas)**: Peer-to-peer lending platform

**Impact on mid-market**:
- Defines operational limits, capital requirements, and governance standards
- SCDs cannot fund operations via deposits — limits growth without creative funding structures
- SEPs must maintain segregated accounts for investors
- Both must report to SCR and comply with BCB prudential requirements

**AI/Data implications**:
- Automated credit decisioning must be auditable and explainable per BCB guidance
- All credit operations must be reported to SCR — automation critical for compliance
- Customer data handling must comply with both BCB and LGPD requirements

### BCB Resolution 4.893 — Open Finance (Open Banking)

**What it does**: Mandates data sharing across financial institutions upon customer consent. Implemented in phases:
- Phase 1: Institutional data (products, channels)
- Phase 2: Customer data (accounts, transactions, credit cards)
- Phase 3: Payment initiation (PIX, TED)
- Phase 4: Credit data, insurance, investments, foreign exchange

**Impact on mid-market**:
- Fintechs can access customer financial data from incumbents (with consent)
- Enables enriched credit scoring using transaction history across institutions
- Mandatory participation for regulated institutions above threshold
- Smaller fintechs can participate as "data recipients" without full reciprocity requirements

**AI/Data implications**:
- Creates massive new data source for ML credit models
- Consent management must be automated and auditable
- Data standardization (Open Finance APIs) simplifies integration
- Real-time data access enables dynamic credit limit adjustments

### SCR (Sistema de Informações de Crédito) Reporting

**What it does**: Brazil's credit information system operated by BCB. All financial institutions must report:
- Credit operations above R$200 (reduced from R$1,000)
- Monthly reporting deadline (D+15 after month-end)
- Borrower risk classification (AA to H scale)

**Impact on mid-market**:
- Monthly reporting obligation for every credit operation — significant operational burden
- Data quality issues trigger BCB supervisory actions
- SCR data is the primary input for credit bureau scores
- Fintechs can query SCR for credit decisions (with borrower authorization)

**AI/Data implications**:
- Automated SCR reporting eliminates monthly compliance crises
- SCR query automation speeds credit analysis
- Risk classification models must align with BCB's AA-H scale
- Data reconciliation between internal systems and SCR is a persistent pain point

### PIX Regulation

**What it does**: BCB-regulated instant payment system with growing ecosystem:
- PIX standard payments (instant, 24/7, free for individuals)
- PIX Cobrança (billing/invoicing)
- PIX Garantias (collateral/guarantee — emerging)
- PIX Automático (recurring payments — launched 2024)

**Impact on mid-market**:
- PIX transaction data becomes a credit signal (payment behavior, cash flow patterns)
- PIX Automático enables automated loan repayment collection
- PIX Garantias may enable new collateral types for lending
- Real-time payment data enables dynamic credit limit management

### LGPD (Lei Geral de Proteção de Dados)

**What it does**: Brazil's data protection law (equivalent to GDPR). Key provisions for financial services:
- Consent required for data processing (except legitimate interest, legal obligation, credit protection)
- Data minimization, purpose limitation, retention limits
- Right to access, correction, deletion, portability
- Data breach notification within "reasonable time" to ANPD
- Credit protection is a legitimate basis for processing — but narrowly interpreted

**Impact on mid-market**:
- Consent management across Open Finance data flows is complex
- Credit bureau data usage requires legitimate interest documentation
- Customer data portability intersects with Open Finance obligations
- Data retention policies must balance credit analysis needs with minimization principles

**AI/Data implications**:
- ML model training on personal data requires purpose specification and legal basis
- Automated credit decisions must provide explanation to the customer upon request
- Open Finance data received under consent cannot be retained beyond consent scope
- Data anonymization/pseudonymization for model training is recommended

### Resolução CVM 175/2022 — New FIDC Framework

**What it does**: Modernized FIDC regulation:
- Simplified structure (single class of quotas allowed)
- Expanded eligible assets (including litigation receivables, crypto assets)
- Enhanced governance and risk management requirements
- Mandatory mark-to-market for credit portfolio

**Impact on mid-market**:
- More FIDCs entering market = more demand for credit analytics and portfolio monitoring
- Mark-to-market requirement creates need for real-time credit quality assessment
- Enhanced governance requires better data infrastructure for reporting
- Opens FIDC to retail investors — increases scrutiny and compliance requirements

## Compliance Requirements Matrix

| Requirement | Frequency | Owner | Current Process | Automation Opportunity |
|------------|-----------|-------|-----------------|----------------------|
| SCR reporting | Monthly (D+15) | Operations/Compliance | Semi-automated, spreadsheet reconciliation | Full automation with data validation |
| e-Financeira (Receita Federal) | Semi-annual | Compliance/Finance | Manual data extraction and formatting | Automated extraction from core banking |
| BCB risk classification (AA-H) | Monthly (with SCR) | Credit/Risk | Manual classification per policy | ML-assisted classification with audit trail |
| COAF suspicious transaction reports | Event-driven | Compliance | Manual review and filing | Rule-based + ML anomaly detection |
| LGPD consent management | Continuous | DPO/Compliance | Basic consent forms; limited tracking | Automated consent lifecycle management |
| Open Finance API availability | Continuous (99.5% SLA) | IT/Engineering | Monitoring dashboards | Automated alerting and failover |
| CVM FIDC reporting | Monthly/Quarterly | Fund admin | Manual report generation | Automated portfolio analytics and reporting |
| AML/KYC screening | Per customer (onboarding + periodic) | Compliance | Manual screening against sanctions lists | Automated screening with continuous monitoring |

## Regulatory Timeline (2025-2027)

| Date | Event | Impact | Preparation Needed |
|------|-------|--------|-------------------|
| 2025 H2 | Open Finance Phase 4 expansion | Credit data sharing across institutions | API integration, consent management |
| 2025-2026 | ANPD enforcement ramp-up | Fines for LGPD non-compliance | Data governance framework, consent automation |
| 2026 | PIX Garantias full rollout | New collateral types for lending | Payment system integration, collateral management |
| 2026 | BCB enhanced SCR requirements | More granular reporting fields | SCR reporting system upgrade |
| 2026-2027 | CVM FIDC regulation full implementation | Enhanced governance and reporting | Portfolio analytics, mark-to-market automation |
| 2027+ | BCB AI governance framework (expected) | Explainability requirements for credit models | Model documentation, audit trails, bias testing |

## Regulatory Risk Assessment

### High Risk (Immediate Action Needed)

- **SCR reporting accuracy** — BCB supervisory actions for data quality issues; fines and operational restrictions
- **LGPD consent for Open Finance data** — ANPD fines up to 2% of revenue; reputational damage
- **AML/KYC compliance** — COAF penalties; potential license revocation

### Medium Risk (12-Month Horizon)

- **Open Finance API compliance** — BCB penalties for non-participation or SLA failures
- **CVM FIDC reporting** — enhanced requirements under Resolução 175; fund suspension risk
- **BCB model governance** — expected framework will require explainability and bias documentation

### Low Risk (Monitor)

- **PIX Garantias regulation** — still emerging; early adoption is optional
- **ESG reporting for financial institutions** — BCB GRSAC requirements expanding but timeline unclear

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
