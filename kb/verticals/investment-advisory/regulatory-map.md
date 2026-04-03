---
title: "Investment Advisory — Regulatory Map"
type: regulatory-map
vertical: investment-advisory
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: monthly
tags: [investment-advisory, regulatory, compliance, CVM, ANBIMA, LGPD]
---

# Investment Advisory — Regulatory Map

## Regulatory Bodies

| Agency | Jurisdiction | Key Role |
|--------|-------------|----------|
| CVM (Comissão de Valores Mobiliários) | Securities markets | Primary regulator for investment advisors, suitability, disclosures |
| ANBIMA (Associação Brasileira das Entidades dos Mercados Financeiro e de Capitais) | Industry self-regulation | Distribution code, suitability standards, advertising rules |
| ANPD (Autoridade Nacional de Proteção de Dados) | Data protection | LGPD enforcement, DPO requirements |

## Key Legislation

| Regulation | Date/Status | Summary | Impact on Clients |
|-----------|-------------|---------|-------------------|
| **CVM 178 (2023)** | In effect | Renamed category to "assessor de investimento"; ended platform exclusivity; flexible corporate structures; mandatory diretor responsável; termo de ciência required | Enables multi-platform operations (XP+BTG); requires governance updates; operational restructuring |
| **CVM 179** | Fully effective November 2024 | Mandatory disclosure of all rebates, spreads, and distribution fees at point of sale; quarterly fee extracts to clients | Forces transparency; accelerates fee-based model shift; clients see total cost for first time |
| **CVM 30/2021** | In effect | Suitability verification mandatory before any recommendation; three-element assessment (objectives, financial situation, knowledge) | Every recommendation must be documented and justified; creates compliance burden but also automation opportunity |
| **CVM 50/2021** | In effect | Client registration and KYC requirements; maximum 5-year profile update cycle; investor classification: professional (>R$10M), qualified (>R$1M) | Profile data must be current; classification determines product access; creates data management obligations |
| **ANBIMA Código de Distribuição** | In effect | Standardized suitability scoring, product complexity classification, advertising rules, privacy controls | Operational standards beyond CVM minimums; self-regulatory compliance expected by platforms |
| **LGPD** | In effect | Purpose limitation for suitability data; DPO required; incident response plan; client right to access, correct, and delete personal data | Every data pipeline must include consent management and audit trails; constrains data usage for AI models |

## Compliance Requirements

### Mandatory Reporting and Disclosures

- **CVM 179 — Point-of-sale disclosure**: All rebates, spreads, and distribution fees must be disclosed to the client at the moment of recommendation
- **CVM 179 — Quarterly extracts**: Clients must receive quarterly statements detailing all fees and commissions earned by the escritório
- **CVM 30 — Suitability documentation**: Every investment recommendation must be preceded by suitability verification covering three elements: investment objectives, financial situation, and client knowledge
- **CVM 50 — Client profile updates**: KYC profiles must be updated at least every 5 years; investor classification (professional >R$10M, qualified >R$1M) determines product eligibility
- **CVM 178 — Termo de ciência**: Clients must sign a termo de ciência (acknowledgment term) regarding the advisory relationship

### Data Protection (LGPD)

- **Purpose limitation**: Suitability data collected under CVM 30 can only be used for the stated purpose (investment suitability verification) — repurposing for marketing or AI training requires separate consent
- **DPO requirement**: Every escritório must designate a Data Protection Officer
- **Incident response plan**: Mandatory plan for data breach notification
- **Client rights**: Right to access, correct, and delete personal data held by the escritório
- **Consent management**: Every data pipeline (especially Open Finance integrations via Pluggy) must implement explicit consent capture and audit trails
- **AI model implications**: Training AI models on client data requires careful consent architecture; anonymization may be required for aggregate analytics

### Industry-Specific Requirements

- **Diretor responsável** (CVM 178): Every escritório must designate a responsible director accountable for regulatory compliance
- **ANBIMA suitability scoring**: Standardized scoring methodology beyond CVM minimums
- **ANBIMA product complexity classification**: Products classified by complexity level affecting disclosure requirements
- **ANBIMA advertising rules**: Marketing content must comply with ANBIMA advertising guidelines

## Compliance Calendar

| Frequency | Obligation | Regulation | Risk of Non-Compliance |
|-----------|-----------|------------|------------------------|
| Every transaction | Disclose rebates/spreads/distribution fees | CVM 179 | Fines up to R$20M for CVM violations |
| Quarterly | Fee extract delivery to all clients | CVM 179 | CVM sanctions, client trust erosion |
| Before every recommendation | Suitability verification | CVM 30 | CVM sanctions, client liability |
| Every 5 years (max) | Client profile update / KYC | CVM 50 | Product eligibility errors, regulatory exposure |
| Ongoing | LGPD consent management | LGPD | ANPD fines, reputational damage |
| Ongoing | Anti-churning monitoring | CVM 30 / ANBIMA | Suitability violations |
| Ongoing | Continuous suitability drift detection | CVM 30 / ANBIMA | Misaligned portfolios |

## Automation Opportunities

| Process | Current State | Automated State | Time Savings |
|---------|--------------|-----------------|-------------|
| CVM 179 disclosure generation | Manual at point of sale | Automated disclosure attached to every recommendation | 2–4 hrs/week per advisor |
| Quarterly fee extracts | Manual compilation from platform data | Automated pipeline from XP/BTG APIs | 20–40 hrs/quarter |
| Suitability verification | Annual or ad hoc review | Continuous monitoring with automated drift alerts | 10–15 hrs/week for compliance officer |
| KYC profile freshness | Manual tracking in spreadsheets | Automated alerts for upcoming 5-year expirations | 5–10 hrs/month |
| LGPD consent management | Manual consent tracking | Automated consent capture, storage, and audit trail | 5–8 hrs/month |
| Anti-churning detection | No systematic monitoring | ML-based pattern detection with automated flags | Prevents CVM sanctions |

## Recent Changes

- **CVM 179 (November 2024)**: Full enforcement of commission transparency — the most impactful regulatory change in recent years, fundamentally changing the client-advisor dynamic
- **CVM 178 (2023)**: End of platform exclusivity enables multi-platform advisory, increasing data integration complexity

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-05-02*
