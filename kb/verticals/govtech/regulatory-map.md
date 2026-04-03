---
title: "GovTech — Regulatory Map"
type: regulatory-map
vertical: govtech
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: monthly
tags: [govtech, regulatory, compliance, Lei-14133, PNCP, TCU, CGU, LAI, LGPD]
---

# GovTech — Regulatory Map

## Regulatory Bodies

| Agency | Jurisdiction | Key Role | Digital Systems |
|--------|-------------|----------|-----------------|
| **TCU** (Tribunal de Contas da Uniao) | Federal | External audit of federal spending and transfers | Alice (edital analysis AI), Adele (audit assistant), e-TCU |
| **CGU** (Controladoria-Geral da Uniao) | Federal | Internal control, anti-corruption, transparency | Portal da Transparencia, Fala.BR, e-OUV |
| **Ministerio da Gestao e Inovacao** | Federal | Procurement policy, PNCP administration | PNCP, ComprasNet (legacy), SICAF |
| **TCEs** (Tribunais de Contas Estaduais) | State (26 + 4 TCMs) | External audit of state and municipal spending | Varies by state -- e-Sfinge (SC), Sagres (PB), FIPLAN (BA) |
| **Controladorias Estaduais/Municipais** | State/Municipal | Internal control at state/municipal level | Varies widely |
| **AGU** (Advocacia-Geral da Uniao) | Federal | Legal opinions on procurement disputes | SAPIENS |
| **ANPD** (Autoridade Nacional de Protecao de Dados) | Federal | LGPD enforcement for government data systems | ANPD portal |

## Key Legislation

| Law/Regulation | Date | Summary | Impact on Clients |
|---------------|------|---------|-------------------|
| **Lei 14.133/2021** (Nova Lei de Licitacoes) | Apr 2021 | Replaces Lei 8.666/1993, Lei 10.520/2002 (Pregao), Lei 12.462/2011 (RDC). Creates PNCP, new modalities (dialogo competitivo), digital-first procurement | All procurement entities must adopt; creates centralized data opportunity via PNCP API |
| **Lei 8.666/1993** (legacy) | Jun 1993 | Original procurement law, still referenced for contracts initiated before Lei 14.133 transition | Historical reference for auditing older contracts; coexistence period ended Dec 2023 |
| **Lei 12.527/2011** (LAI - Lei de Acesso a Informacao) | Nov 2011 | Guarantees citizen access to public information; mandates proactive data publication | Government entities must publish procurement data; enables transparency tools |
| **Lei 13.709/2018** (LGPD) | Aug 2018 | Data protection law. Government entities processing personal data must comply | Limits how procurement data involving individuals can be used; requires DPO |
| **Lei 8.429/1992** (Lei de Improbidade Administrativa) | Jun 1992 | Administrative misconduct including procurement fraud; updated by Lei 14.230/2021 | Creates accountability framework; AI tools can help detect improbidade patterns |
| **LC 101/2000** (Lei de Responsabilidade Fiscal - LRF) | May 2000 | Fiscal discipline for public entities; spending limits, transparency requirements | TCEs audit LRF compliance; creates demand for fiscal monitoring dashboards |
| **Lei 12.846/2013** (Lei Anticorrupcao) | Aug 2013 | Corporate liability for corruption in government procurement | Private companies need compliance tools; drives due diligence demand |
| **Decreto 8.777/2016** (Dados Abertos) | May 2016 | Open data policy for federal government | Mandates machine-readable publication of government datasets |
| **Decreto 11.260/2022** (EGD governance) | Nov 2022 | Governance framework for Estrategia de Governo Digital 2024--2027 | Sets digital transformation targets and interoperability mandates |

## PNCP Mandates and Timelines

The Portal Nacional de Contratacoes Publicas (PNCP) is the centerpiece of Lei 14.133/2021:

| Requirement | Deadline | Status | Impact |
|------------|----------|--------|--------|
| Federal entities: publish all procurement on PNCP | Mandatory since Apr 2023 | Active | Federal procurement data accessible via API |
| State/DF entities: publish on PNCP | Mandatory since Apr 2023 | Partial adoption | Uneven compliance across states |
| Municipal entities (pop >100K): publish on PNCP | Mandatory since Apr 2023 | Partial adoption | Larger municipalities adopting |
| Municipal entities (pop <100K): publish on PNCP | Mandatory since Apr 2024 | Low adoption | Smallest municipalities lag significantly |
| Full transition from Lei 8.666 to Lei 14.133 | Dec 2023 (new contracts) | Ongoing | Coexistence period ended; new contracts under new law |

**PNCP API capabilities**: The PNCP API provides access to procurement notices (editais), contracts, atas de registro de preco, and supplier data. Endpoints include search by CNPJ, item category (CATMAT/CATSER), date range, procurement modality, and entity.

## Open Data Requirements

| Obligation | Legal Basis | Who Must Comply | Data Available |
|-----------|-------------|----------------|----------------|
| Proactive transparency (receitas, despesas, licitacoes) | Lei 12.527/2011 Art. 8 | All public entities | Budget execution, procurement, personnel |
| Open data in machine-readable formats | Decreto 8.777/2016 | Federal entities | Datasets on dados.gov.br |
| PNCP publication | Lei 14.133/2021 Art. 174 | All procurement entities | Editais, contracts, atas, supplier data |
| Diario Oficial publication | Various | All public entities | Official acts, procurement notices, appointments |
| Portal da Transparencia | LC 131/2009 (Transparencia) | All entities receiving federal transfers | Real-time budget execution data |

## Procurement Modalities (Lei 14.133/2021)

| Modality | Use Case | Threshold | Key Characteristics |
|----------|----------|-----------|-------------------|
| **Pregao** (eletronico) | Common goods and services | No threshold (most used) | Reverse auction; mandatory electronic form |
| **Concorrencia** | Works, services, purchases above thresholds | Above R$1.43M (works), R$359K (goods/services) | Open competition; technical + price criteria |
| **Concurso** | Technical/artistic/scientific work | No threshold | Jury-based selection |
| **Leilao** | Sale of public assets | No threshold | Highest bid wins |
| **Dialogo competitivo** (new) | Complex, innovative solutions | No threshold | Multi-phase negotiation; new under Lei 14.133 |
| **Dispensa** | Small purchases, emergency | Below R$59K (goods/services), R$119K (works) | Simplified process; still requires PNCP publication |
| **Inexigibilidade** | Sole source, unique provider | No threshold | Justification required; published on PNCP |

## Compliance Calendar

| Period | Obligation | Agency | Notes |
|--------|-----------|--------|-------|
| Daily | PNCP publication of new procurement | All entities | Editais, awards, contracts must be published |
| Monthly | Budget execution update on Portal da Transparencia | Federal entities | Real-time requirement under LC 131/2009 |
| Annual | Prestacao de Contas to TCE/TCU | All entities | Comprehensive accountability report |
| Annual | Open data plan update | Federal entities | Decreto 8.777/2016 compliance |
| Ongoing | LAI request response (20 days + 10 extension) | All entities | Lei 12.527/2011 deadline |
| Ongoing | LGPD compliance for personal data in procurement | All entities | ANPD oversight |
| Per process | Publication of all procurement phases on PNCP | All entities | Lei 14.133/2021 requirement |

## Automation Opportunities

| Process | Current State | Automation Potential | Estimated Savings |
|---------|--------------|---------------------|-------------------|
| Edital analysis for compliance | Manual review by auditors/lawyers | LLM-powered edital parsing and red-flag detection | 80--90% reduction in screening time |
| Supplier due diligence | Manual CEIS/CNEP/CADIN checks | Automated cross-reference with all sanction databases | Hours to seconds per supplier check |
| Price benchmarking | Manual comparison across historical procurement | ML-powered price prediction using PNCP/CATMAT data | 10--20% savings through accurate estimation |
| Procurement opportunity monitoring | Manual portal checking or basic keyword alerts | Agent-based monitoring across PNCP + state portals | 40--60% more opportunities identified |
| TCE audit screening | Manual sampling of contracts | AI-powered anomaly detection across 100% of contracts | 10--50x increase in audit coverage |
| LRF compliance monitoring | Manual fiscal indicator calculation | Automated dashboards with alert thresholds | Continuous vs. periodic monitoring |

## Recent Changes

- **2024**: PNCP adoption expanding to smaller municipalities (pop <100K mandatory since Apr 2024)
- **2023**: Lei 14.133/2021 full enforcement for new contracts (Dec 2023 transition deadline)
- **2022**: Decreto 11.260/2022 establishing EGD 2024--2027 governance framework
- **Ongoing**: TCU expanding Alice/Adele AI capabilities; state TCEs seeking similar tools

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-05-02*
