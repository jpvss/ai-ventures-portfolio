---
title: "GovTech — Sales Playbook"
type: sales-playbook
vertical: govtech
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [govtech, sales, hooks, objections, pricing, ICP, dual-track]
---

# GovTech — Sales Playbook

## Ideal Client Profile (ICP)

### Track 1: Government Entities

| Attribute | Criteria |
|-----------|---------|
| Entity Type | Tribunais de Contas Estaduais, Controladorias, Secretarias de Fazenda, large Prefeituras |
| Annual Budget | R$100M+ (state secretarias), R$50M+ (municipal) |
| Audit Volume | R$1B+ in annual procurement under audit (for TCEs) |
| Digital Maturity | PNCP-publishing, SEI-adopting, but lacking AI/analytics capabilities |
| Pain Indicators | Low audit coverage (<5%), manual edital analysis, reactive fraud detection, no PNCP analytics |
| Decision Maker | Presidente do TCE, Controlador-Geral, Secretario de Fazenda |
| Budget Holder | Presidente do TCE or Secretario de Administracao; innovation funds via ENAP/BID |
| Geography | Priority states: SP, MG, RJ, RS, PR, BA, PE (largest procurement volumes) |

### Track 2: Private Companies

| Attribute | Criteria |
|-----------|---------|
| Revenue from Gov | R$10M+ annually in government contracts |
| Industry | Insurance (seguro garantia), construction, IT services, medical supplies, facilities management |
| Operations | Bids on procurement across multiple states/municipalities |
| Pain Indicators | Manual portal monitoring, missed opportunities, slow edital analysis, compliance gaps |
| Decision Maker | Commercial Director, Compliance Officer, CEO |
| Budget Holder | Commercial or Operations budget |

## Sales Hooks

### Hook 1: "Your auditors are reviewing 1% of contracts. AI can screen 100% and flag the 5% that matter."

**Context:** Use with TCE Presidente or Conselheiro. Every TCE knows their coverage rate is embarrassingly low relative to the volume of procurement they're supposed to audit.
**Supporting Data:** Most mid-size TCEs audit 2--5% of procurement contracts through manual sampling. TCU's Alice system has demonstrated that AI can screen 100% of editais for irregularities, flagging the highest-risk 3--5% for human review. State TCEs lack the budget and team to replicate Alice in-house.
**Follow-up Question:** "What is your current audit coverage rate? How do you prioritize which contracts to review? How many potential irregularities do you estimate slip through?"

### Hook 2: "You're missing 40--60% of relevant procurement opportunities because they're buried across portals."

**Context:** Use with Commercial Directors at companies selling to government. Works especially well with insurance brokers (seguro garantia) where each missed edital is a lost commission.
**Supporting Data:** Procurement opportunities are scattered across PNCP, ComprasNet (legacy), 26 state portals, and 5,570 municipal Diarios Oficiais. Manual monitoring covers a fraction. Our licitaleads platform demonstrated that AI-powered aggregation increases opportunity detection by 40--90%.
**Follow-up Question:** "How many people do you have monitoring procurement portals? How many portals do they check daily? When was the last time you learned about a relevant edital after the deadline had passed?"

### Hook 3: "Lei 14.133 created the first centralized procurement database. The question is: who builds intelligence on top of it?"

**Context:** Use with GovTech startup founders or innovation-minded government leaders. The PNCP API is a game-changer but few are exploiting it.
**Supporting Data:** PNCP is the first time Brazil has a single, API-accessible procurement database covering R$800B+ in annual spending. Early movers who build AI intelligence on this data will have a 2--3 year structural advantage as more entities publish and data depth grows.
**Follow-up Question:** "Are you consuming PNCP API data today? What intelligence are you building on top of it? What would you build if you had a data engineering team available tomorrow?"

### Hook 4: "One fraudulent contract costs more than 10 years of AI audit investment."

**Context:** Use with Controladores or TCE leadership when discussing budget for AI tools. The ROI math is overwhelming.
**Supporting Data:** A single fraudulent procurement contract in a mid-size state can involve R$10--100M+. An AI audit platform costs R$200K--R$500K to build and R$10K--R$30K/month to maintain. TCU's Alice has flagged billions in irregularities. The question is not whether AI for audit pays off -- it's how fast.
**Follow-up Question:** "What was the largest irregularity your TCE detected last year? How was it discovered -- proactively or through a denuncia? What would it mean to detect those patterns automatically?"

### Hook 5: "Your prestacao de contas takes months. It should take days."

**Context:** Use with Secretarios de Fazenda or Controladores at municipal/state level. Prestacao de contas is a universally painful annual process.
**Supporting Data:** Annual prestacao de contas preparation typically consumes 2--4 months of staff time across finance, procurement, and administrative departments. Automated data integration from SIAFI, procurement systems, and financial execution databases can reduce preparation to 1--2 weeks with human review.
**Follow-up Question:** "How long does your annual prestacao de contas take to prepare? How many staff are involved? Have you ever had a TCE finding that could have been caught during preparation?"

## Objection Handling

| Objection | Response | Evidence |
|-----------|----------|----------|
| "Government procurement of consulting is slow" | Our diagnostic fits under the dispensa de licitacao threshold (R$59K under Lei 14.133 Art. 75, II). Start there, prove value in 2--3 weeks, then the larger implementation has a business case for the formal procurement process. | Lei 14.133/2021 dispensa thresholds |
| "We can't use AI for official audit decisions" | AI doesn't replace auditors -- it triages. 100% automated screening surfaces the top 5% for human review. The auditor makes every decision. TCU uses Alice/Adele exactly this way. | TCU precedent with Alice/Adele |
| "We don't have budget" | The diagnostic is R$25K--R$75K, potentially under dispensa. Innovation funds (ENAP, BID, Banco Mundial) often have GovTech allocation. The ROI case from the diagnostic builds the justification for the implementation budget. | ENAP innovation programs, BID funding |
| "Our data isn't integrated enough" | That's exactly our expertise. We aggregate PNCP + Portal da Transparencia + sanction databases + your local systems. Data integration is what we do, not a prerequisite. | licitaleads and ceap-deputy-expenses as proof |
| "We tried technology projects before and they failed" | Government IT projects fail when they're built as monoliths over 2+ years. Our diagnostic-first model delivers value in 2--3 weeks. Each implementation phase (6--16 weeks) delivers a working product. Fail fast, learn fast. | Modular engagement model |
| "Free tools already exist (Portal da Transparencia, Querido Diario)" | Those are data sources, not intelligence tools. We build the LLM-powered analysis, anomaly detection, and actionable alerts on top of those sources. It's the difference between a library and a research assistant. | Data source vs. intelligence distinction |

## Dual-Track Selling Strategy

GovTech is unique in having two distinct buyer tracks that require different approaches:

### Government Track

- **Entry**: Innovation events (BrazilLAB Demo Day, ENAP workshops, TCE conferences)
- **Champion**: Tech-savvy auditor or Controlador seeking modernization
- **Procurement path**: Dispensa for diagnostic (< R$59K) -> licitacao for implementation
- **Timeline**: 3--6 months from first contact to diagnostic; 6--12 months to implementation procurement
- **Key risk**: Political transition can kill projects; build relationship with career staff, not political appointees

### Private Sector Track

- **Entry**: Insurance broker associations (CNSeg events), government supplier conferences, LinkedIn/outbound
- **Champion**: Commercial Director frustrated with missed opportunities
- **Procurement path**: Standard B2B commercial contract
- **Timeline**: 2--4 weeks from first contact to diagnostic; 4--8 weeks to implementation contract
- **Key risk**: Price sensitivity; demonstrate ROI quickly with specific missed-opportunity examples

## Discovery Call Framework

### Questions to Ask (Government)

1. "What is your current audit coverage rate for procurement contracts?"
2. "How do you detect procurement irregularities -- proactively or through denuncias?"
3. "What is your PNCP integration status? Are you publishing and consuming data?"
4. "How long does prestacao de contas preparation take?"
5. "Have you explored AI tools like TCU's Alice for audit assistance?"
6. "What innovation or digital transformation budget is available?"

### Questions to Ask (Private)

1. "How many procurement portals does your team monitor daily?"
2. "What percentage of relevant editais do you estimate you're catching?"
3. "How long does it take to analyze an edital and make a bid/no-bid decision?"
4. "How do you verify that your suppliers/subcontractors are not on CEIS/CNEP?"
5. "When was the last time you lost a deal because you found out about the edital too late?"
6. "What is your seguro garantia volume and how do you source opportunities?"

### Red Flags (Disqualifiers)

- Government entity with budget below R$20M (insufficient scale)
- Private company with less than R$5M in government contracts (insufficient volume)
- No executive sponsorship (purely IT-driven inquiry in government)
- Entity in active political crisis or leadership transition
- Requirement to use a specific technology stack that conflicts with our architecture

### Green Flags (High-Fit Indicators)

- TCE with explicit modernization mandate from new Presidente
- Private company that recently missed a major contract they didn't know about
- Entity attending BrazilLAB or ENAP innovation events
- Controlador or auditor who references TCU's Alice as inspiration
- Company with growing government contract portfolio but static monitoring staff
- Post-election new administration seeking transparency wins

## Pricing Strategy

| Engagement | Price | Value Anchor | ROI Multiple |
|-----------|-------|-------------|-------------|
| Diagnostic (Government) | R$25K--R$75K | Under dispensa threshold; less than one auditor's annual cost | N/A (discovery) |
| Diagnostic (Private) | R$25K--R$50K | Less than one missed procurement opportunity | N/A (discovery) |
| Procurement Intelligence | R$100K--R$250K | 2--5 additional won contracts per quarter | 200--500% Year 1 |
| Audit Intelligence | R$200K--R$500K | R$50M+ in detected irregularities per R$5B audited | 100--250x |
| Transparency Dashboard | R$80K--R$200K | Accountability + political capital | Strategic value |
| Compliance Monitor | R$100K--R$250K | Avoids Lei 12.846 penalties (up to 20% gross revenue) | Risk mitigation |
| Monthly Retainer | R$10K--R$30K/mo | Ongoing intelligence + platform maintenance | Maintenance |

## Proof Points

- **licitaleads**: Live procurement intelligence platform for insurance brokers; 2x opportunity detection improvement
- **ceap-deputy-expenses**: Live transparency dashboard using API Dados Abertos da Camara; demonstrates public data analytics capability
- **licenciaminer**: Environmental licensing intelligence cross-referencing with procurement data; demonstrates cross-domain integration
- **TCU Alice/Adele**: External validation that AI for government audit works at scale
- **PNCP API**: Government's own investment in data centralization validates the market thesis
- **BrazilLAB ecosystem**: 100+ GovTech startups validating market demand

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
