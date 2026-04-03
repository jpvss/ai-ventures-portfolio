---
title: "Education & HR — Regulatory Map"
type: regulatory-map
vertical: education-hr
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [education-hr, regulation, CLT, eSocial, LGPD, MEC, SINE, compliance]
---

# Education & HR — Regulatory Map

## Regulatory Overview

The Education & HR vertical operates under a dense regulatory framework spanning labor law (CLT/eSocial), data protection (LGPD), education regulation (MEC), and public employment services (SINE/MTE). For AI consulting engagements, the critical regulatory constraints are LGPD compliance for candidate data processing, eSocial data format standards, and emerging AI-in-hiring regulations.

## Primary Regulatory Bodies

| Agency | Jurisdiction | Relevance to AI Consulting |
|--------|-------------|---------------------------|
| Ministério do Trabalho e Emprego (MTE) | Labor law enforcement, RAIS/CAGED data, SINE | Primary source of employment data; regulates employment agencies |
| ANPD (Autoridade Nacional de Proteção de Dados) | LGPD enforcement | All candidate data processing requires LGPD compliance |
| MEC (Ministério da Educação) | Education quality, accreditation, INEP data | Regulates EdTechs, defines quality metrics, publishes education data |
| INEP | Education statistics, ENEM, IDEB, Censo da Educação | Key data source for education-employment correlation analysis |
| Justiça do Trabalho (TST/TRTs) | Labor dispute resolution | Jurisprudence on AI-based hiring decisions, discrimination claims |
| CREA/CRA/OAB (Professional Councils) | Professional credential validation | Must be considered in credential verification systems |

## Key Legislation

### 1. CLT (Consolidação das Leis do Trabalho) — Decreto-Lei 5.452/1943

**Relevance**: Foundation of Brazilian employment law; governs hiring, contracts, termination.

**Key provisions affecting AI solutions**:
- **Art. 373-A**: Prohibits gender discrimination in hiring — AI screening must be auditable for bias
- **Art. 442-B**: Defines autonomous worker relationship — relevant for gig/platform classifications
- **Art. 461**: Equal pay for equal work — salary prediction models must account for legal parity requirements
- **Art. 482/483**: Just cause termination criteria — attrition prediction models must not create self-fulfilling prophecies

**Compliance requirements for AI systems**:
- Screening algorithms must not discriminate by gender, race, age, disability, or other protected classes
- Automated rejection decisions should be auditable and explainable
- Human review required for consequential employment decisions (hiring, termination, promotion)

### 2. LGPD (Lei 13.709/2018) — Data Protection

**Relevance**: Governs all processing of candidate personal data, including CV analysis, profiling, and automated decisions.

**Key provisions**:
- **Art. 7 (Legal bases)**: Candidate data processing typically requires consent (Art. 7-I) or legitimate interest (Art. 7-IX)
- **Art. 11 (Sensitive data)**: Race, health, biometrics, political/religious affiliation — cannot be used for screening without explicit consent
- **Art. 12 (Anonymization)**: Anonymized data is not subject to LGPD — relevant for aggregate analytics
- **Art. 20 (Automated decisions)**: Data subjects have the right to request review of automated decisions that affect their interests — AI screening must support human review
- **Art. 46 (Security)**: Technical and administrative measures required to protect personal data

**Compliance framework for AI recruitment systems**:
1. **Consent management**: Clear, specific consent for AI-based CV analysis; separate consent for profiling
2. **Data minimization**: Process only data necessary for the stated purpose (no scraping social media without consent)
3. **Right to explanation**: Must be able to explain why a candidate was rejected/ranked — black-box models are high risk
4. **Data retention**: Define and enforce retention periods for candidate data (typically 6-24 months post-application)
5. **DPIA (Data Protection Impact Assessment)**: Required for large-scale profiling of candidates
6. **DPO appointment**: Companies processing candidate data at scale need a designated DPO

### 3. eSocial (Decreto 8.373/2014)

**Relevance**: Mandatory electronic system for reporting employment events to government. Creates structured employment data.

**Key events relevant to AI systems**:
- **S-2200**: Admissão do trabalhador (hiring event) — structured hiring data
- **S-2206**: Alteração contratual (contract changes) — salary changes, promotions
- **S-2299**: Desligamento (termination) — turnover data with reason codes
- **S-2240**: Condições ambientais do trabalho (work conditions)
- **S-1200**: Remuneração (compensation events) — salary data by function

**Opportunity**: eSocial forces structured data submission, creating a rich dataset for employment analytics. Companies that can leverage this data (rather than just comply with it) gain competitive advantage.

**Integration considerations**: eSocial XML schemas can be parsed to extract employment lifecycle events for ML training data.

### 4. RAIS (Relação Anual de Informações Sociais)

**Relevance**: Annual mandatory census of all formal employment relationships. Gold mine for labor market analytics.

**Data available**:
- Employment by CNAE (industry code), CBO (occupation), municipality
- Salary ranges by occupation and region
- Hiring and termination volumes by month
- Employer size and sector distribution
- Worker demographics (age, education level, gender)

**Access**: Public microdata available from MTE/Portal Emprega Brasil. Aggregated data freely accessible; microdata requires request.

**AI applications**: Salary prediction, labor market trend analysis, skills demand forecasting, regional employment mapping.

### 5. CAGED (Cadastro Geral de Empregados e Desempregados)

**Relevance**: Monthly registry of formal job admissions and terminations. More timely than RAIS (monthly vs. annual).

**Data available**: Real-time formal employment flow data — admissions, terminations, by sector, occupation, and municipality.

**AI applications**: Near-real-time labor market signals for recruitment timing, industry health indicators, emerging occupation trends.

### 6. CBO (Classificação Brasileira de Ocupações)

**Relevance**: Official taxonomy of 2,500+ occupations with descriptions, competencies, and requirements. Essential for skills standardization.

**Structure**: 
- 10 major groups → 47 sub-major groups → 192 minor groups → 596 unit groups → 2,500+ occupations
- Each occupation has: description, main activities, required training, working conditions

**AI applications**: Skills taxonomy backbone for candidate-job matching; competency mapping for gap analysis; standardized occupation labels for ML models.

### 7. MEC Regulations (EdTech Specific)

**Key regulations**:
- **Decreto 9.057/2017**: Regulates distance learning (EAD) — defines quality requirements for online education
- **Portaria MEC 2.117/2019**: Allows up to 40% remote content in presencial courses
- **SINAES (Lei 10.861/2004)**: National system for higher education evaluation — defines quality metrics
- **Catálogo Nacional de Cursos Técnicos**: Standardized technical course taxonomy

**Compliance requirements for EdTech AI**:
- AI-generated content must meet MEC quality standards
- Student data protected under both LGPD and MEC privacy requirements (minor protection for K-12)
- Employment outcome claims must be substantiated — AI analytics can help prove these claims

### 8. SINE/MTE (Sistema Nacional de Emprego)

**Relevance**: Public employment service system; employment agencies must be SINE-accredited for certain government contracts.

**Key regulations**:
- **Lei 13.667/2018**: Restructured SINE, created Portal Emprega Brasil
- Employment agencies must register with MTE
- SINE-accredited agencies access government-referred candidates and programs (Seguro-Desemprego, PRONATEC)

**Integration opportunity**: Portal Emprega Brasil APIs for job matching; integration with SINE candidate pools.

## Emerging Regulatory Trends

### AI-Specific Regulation (2025-2027)
- **PL 2338/2023 (Marco Legal da IA)**: Proposed Brazilian AI regulation framework — classifies AI in hiring as "high risk," requiring impact assessments, transparency, and human oversight
- **EU AI Act influence**: Brazil's regulation likely to follow EU precedent, classifying recruitment AI as high-risk with mandatory conformity assessments
- **ANPD AI guidance**: ANPD expected to issue specific guidance on AI and automated decision-making under LGPD Art. 20

### Implications for AI Consulting
1. **Build for auditability from day one**: All AI recruitment systems should log decisions with explanations
2. **Bias testing as standard practice**: Demographic parity testing should be included in every engagement
3. **Human-in-the-loop as design principle**: Final hiring/rejection decisions must involve human review
4. **Documentation culture**: DPIA, model cards, training data documentation — these will likely become mandatory

## Compliance Checklist for AI HR Solutions

| Requirement | Regulation | Priority | Implementation |
|-------------|-----------|----------|---------------|
| Consent for CV processing | LGPD Art. 7/11 | Critical | Consent management module in every ATS integration |
| Right to explanation of AI decisions | LGPD Art. 20 | Critical | Explainability layer (SHAP/LIME) on all scoring models |
| Non-discrimination in screening | CLT Art. 373-A, Constitution | Critical | Bias audit pipeline; demographic parity testing |
| Data retention limits | LGPD Art. 15-16 | High | Automated data lifecycle management |
| eSocial integration compliance | Decreto 8.373/2014 | High | Standard eSocial XML parser as reusable component |
| DPIA for profiling | LGPD Art. 38 | High | Template DPIA for AI recruitment systems |
| DPO designation | LGPD Art. 41 | Medium | Advisory service for clients without DPO |
| MEC quality standards (EdTech) | Decreto 9.057/2017 | Medium | Quality metrics dashboard aligned with MEC indicators |
| SINE registration (agencies) | Lei 13.667/2018 | Low | Integration with Portal Emprega Brasil APIs |

## Regulatory Risk Matrix

| Risk | Probability | Impact | Mitigation |
|------|------------|--------|------------|
| ANPD enforcement action for non-compliant AI screening | Medium (increasing) | High — fines up to 2% of revenue | LGPD compliance-by-design in all solutions |
| Discrimination lawsuit from AI-rejected candidate | Medium | High — reputational + legal costs | Bias testing, human review, explainability |
| PL 2338/2023 passes with strict AI-in-hiring rules | High (2026-2027) | Medium — compliance costs increase | Build audit/transparency features now; position as advantage |
| eSocial schema changes break integrations | Low-Medium | Medium — rework required | Abstract eSocial parsing layer; version management |
| MEC cracks down on unsubstantiated employment claims | Medium | Medium — EdTech client risk | Data-backed outcome tracking as core feature |

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
