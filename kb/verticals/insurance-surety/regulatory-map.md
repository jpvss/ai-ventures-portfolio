---
title: "Insurance & Surety Bonds — Regulatory Map"
type: regulatory-map
vertical: insurance-surety
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: monthly
tags: [insurance-surety, regulatory, compliance, SUSEP, CNSP, OPIN, LGPD]
---

# Insurance & Surety Bonds — Regulatory Map

## Regulatory Bodies

| Agency | Jurisdiction | Key Role | Website |
|--------|-------------|----------|---------|
| **SUSEP** (Superintendência de Seguros Privados) | Insurance supervision | Regulates and supervises insurance, reinsurance, open pension, and capitalization markets | susep.gov.br |
| **CNSP** (Conselho Nacional de Seguros Privados) | Insurance policy | Sets guidelines and norms for the insurance market, including Open Insurance | gov.br/cnsp |
| **ANPD** (Autoridade Nacional de Proteção de Dados) | Data protection | Enforces LGPD across all sectors including insurance | gov.br/anpd |

## Key Legislation

| Law/Regulation | Date | Summary | Impact on Clients |
|---------------|------|---------|-------------------|
| **Circular SUSEP 662/2022** | 2022 | Seguro garantia regulation — defines modalities, underwriting requirements, claims procedures | Art. 28: must evaluate tomador + principal contract during underwriting |
| **Circular SUSEP 710/2024** | 2024 | Operations registration — detailed field-level data for SRO (Sistema de Registro de Operações) | Requires registration with credentialed entities; detailed data fields mandatory |
| **Circular SUSEP 638/2021** | 2021 | Cybersecurity — data processing/storage rules, cloud computing governance | Mandates cybersecurity controls, cloud governance policies |
| **Resolução CNSP 415/2021** | 2021 | Open Insurance — defines participants, data sharing, consent rules | Obligatory for S1/S2 segment insurers; data sharing and consent management required |
| **Lei 14.133/2021** (Arts. 96/101) | 2021 | Nova Lei de Licitações — public procurement bonds | Up to 5% guarantee (10% justified), 30% with step-in clause for large works |
| **Lei 15.040/2024** | Dec 2025 (in force) | Marco Legal dos Seguros — insurance contract law | 25-day proposal response, 30-day claims response, enhanced transparency requirements |
| **LGPD** (Lei 13.709/2018) | 2020 (enforcement) | General Data Protection Law | Up to 2% revenue / R$50M per infraction; consent required; OPIN consent alignment needed |

## Compliance Requirements

### Mandatory Reporting

**SUSEP Reporting (Circular 662/2022 + Circular 710/2024)**:
- Policy and operations data must be registered in the **SRO (Sistema de Registro de Operações)** via credentialed entities
- Circular 710/2024 defines detailed field-level data requirements for each operation registration
- Compliance monitoring is continuous — SUSEP can audit at any time
- Penalties: administrative sanctions, fines, suspension of operations, or revocation of authorization

**Lei 15.040/2024 Response Deadlines**:
- **25-day maximum** for responding to insurance proposals
- **30-day maximum** for responding to claims
- Enhanced transparency in policy terms and conditions
- Non-compliance exposes insurers to civil liability and regulatory action

### Data Protection (LGPD)

- **Consent required** for processing policyholder and tomador personal data
- OPIN consent management must be LGPD-aligned — dual consent framework
- Up to **2% of revenue or R$50M per infraction** for violations
- Data subject rights (access, correction, deletion) must be technically supported
- Data protection impact assessments required for high-risk processing (e.g., automated underwriting decisions)
- Cross-border data transfer restrictions apply to reinsurance arrangements

### Industry-Specific Requirements

**Circular SUSEP 662/2022 — Seguro Garantia Specifics**:
- Art. 28: Insurers **must evaluate the tomador and the principal contract** as part of underwriting — cannot rely solely on broker assessment
- Defines modalities (licitação, execução, judicial, aduaneiro, etc.)
- Claims procedures and documentation requirements specified
- Subrogation rights framework

**Open Insurance (OPIN) — Resolução CNSP 415/2021**:
- **Obligatory participation** for S1 and S2 segment insurers
- Phase 1: Open data (product/channel information)
- Phase 2: Customer data sharing (with consent)
- **Phase 3: Service initiation** — went live in 2025, enabling cross-platform contracting
- FAPI-certified APIs, mTLS, OAuth 2.0, DCR compliance required
- Brazil is a global pioneer in open insurance implementation

## Compliance Calendar

| Period | Obligation | Agency | Penalty for Non-Compliance |
|--------|-----------|--------|---------------------------|
| Continuous | Operations registration in SRO | SUSEP (Circular 710/2024) | Administrative sanctions, fines |
| Continuous | OPIN API availability (S1/S2 insurers) | CNSP/SUSEP | Regulatory sanctions |
| Within 25 days | Proposal response | Lei 15.040/2024 | Civil liability |
| Within 30 days | Claims response | Lei 15.040/2024 | Civil liability, regulatory action |
| Ongoing | LGPD consent management | ANPD | Up to 2% revenue / R$50M |
| Ongoing | Cybersecurity controls | SUSEP (Circular 638/2021) | Administrative sanctions |

## Automation Opportunities

| Process | Current State | Automated State | Estimated Savings |
|---------|--------------|----------------|-------------------|
| SUSEP SRO reporting | Manual data extraction from policy admin | Automated extraction, validation against SUSEP schemas, real-time compliance monitoring | 60% reduction in compliance labor, near-zero reporting errors |
| Underwriting evaluation (Art. 28) | Manual credit bureau lookups, court record checks | AI-powered risk scoring integrating Serasa, Boa Vista, court records, SUSEP history | 70–80% reduction in underwriting time |
| OPIN API compliance | Manual or non-existent | FAPI-certified API gateway with consent management | Enables new acquisition channel; avoids regulatory sanctions |
| Lei 15.040 deadline tracking | Calendar-based / manual | Automated deadline monitoring with escalation alerts | Prevents liability from missed deadlines |
| LGPD consent management | Fragmented across systems | Centralized consent platform aligned with OPIN requirements | Reduces infraction risk |

## Recent Changes

1. **Lei 15.040/2024 entered into force (December 2025)**: The Marco Legal dos Seguros creates entirely new compliance requirements around proposal and claims response times. Insurers must adapt systems and workflows to meet the 25-day and 30-day deadlines.

2. **Open Insurance Phase 3 went live (2025)**: Service initiation capability means customers can contract insurance through any OPIN-connected platform. This fundamentally changes distribution and creates both opportunity and competitive threat.

3. **Circular SUSEP 710/2024**: New detailed field-level requirements for operations registration in the SRO system increase data quality demands on policy admin systems.

4. **Sinistralidade spike to 41.7%**: While not a regulatory change per se, the 16-percentage-point rise in loss ratio is driving SUSEP's attention to underwriting practices and may lead to further regulatory action on risk management standards.

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-05-02*
