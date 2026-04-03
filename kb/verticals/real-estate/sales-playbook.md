---
title: "Real Estate — Sales Playbook"
type: sales-playbook
vertical: real-estate
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [real-estate, sales, hooks, objections, pricing, ICP, incorporadoras]
---

# Real Estate — Sales Playbook

## Ideal Client Profile (ICP)

| Attribute | Criteria |
|-----------|---------|
| Revenue Range | R$50M--R$500M |
| Company Type | Incorporadora with active SPEs, or assessoria de leilao scaling volume |
| Operations | 3+ simultaneous projects (incorporadoras) or 100+ properties/year (assessorias) |
| Employee Count | 10--100 |
| Systems Landscape | Sienge/UAU ERP + Vista CRM + Excel for SPE/valuation |
| Technology Maturity | 4--8 disconnected systems, manual land prospecting, Excel-based SPE accounting |
| Pain Indicators | Slow land acquisition, manual SPE reconciliation, no AVM, manual edital screening |
| Decision Maker | Diretor de Incorporacao, CFO/Controller, or founder (assessorias) |
| Geography | SP, RJ, MG, PR, SC, RS, GO, DF (major metro areas with ITBI data availability) |

## Sales Hooks

### Hook 1: "You're spending 200+ hours/month reconciling SPEs in Excel."

**Context:** Use when talking to CFO or Controller of incorporadoras with 10+ active SPEs. Patrimonio de afetacao compliance is a universal pain point because every CAIXA-financed project requires it.
**Supporting Data:** A 25-SPE incorporadora dedicates 240+ hours/month to manual bank statement reconciliation, NF-e matching, and patrimonio de afetacao verification. That's ~R$600K/year in accounting labor alone, plus audit risk from documentation gaps.
**Follow-up Question:** "How many SPEs are you managing right now? Walk me through your monthly closing process for patrimonio de afetacao compliance."

### Hook 2: "Your competitors are finding land 3x faster with data intelligence."

**Context:** Use with Diretor de Incorporacao or CEO of incorporadoras expanding to new cities. Especially powerful when client recently lost a land opportunity.
**Supporting Data:** Manual land prospecting takes 30--60 days per opportunity. Automated intelligence (ITBI + zoning + demographics) reduces this to 3--7 days. Incorporadoras evaluating 3x more opportunities close 2x more acquisitions per year.
**Follow-up Question:** "How do you source land opportunities today? When was the last time you lost a parcel to a faster competitor?"

### Hook 3: "You're reviewing 50 editais manually while competitors screen 500 with AI."

**Context:** Use with assessoria de leilao founders/directors. The auction volume surge (40%+ since 2023) makes this immediately relevant.
**Supporting Data:** Manual edital screening limits throughput to 50 per batch. AI-powered parsing with matricula analysis and automated valuation enables 500+ per batch -- a 10x multiplier. Better screening improves acquisition margins by 10pp.
**Follow-up Question:** "How many editais do you screen per batch? What's your current hit rate? How many good deals do you think you're missing?"

### Hook 4: "Your property valuations are off by 20--30%. That's R$400K--R$2M in bad acquisitions per year."

**Context:** Use with any player doing property valuation -- incorporadoras (land/unit pricing), assessorias (auction valuation), imobiliarias (listing pricing). Works especially well when client has had a recent bad deal.
**Supporting Data:** Manual CMA with 3--5 comparables has 20--30% variance from market. An AVM using 50K+ ITBI transactions + FipeZAP + hedonic regression reduces this to 8--12%. For assessorias doing 200+ valuations/year, this avoids 8--12 overpriced acquisitions.
**Follow-up Question:** "How do you value properties today? How many comparables do you typically use? Do you have access to ITBI transaction data?"

### Hook 5: "SREI is making cartorio data machine-readable for the first time. Are you capturing that advantage?"

**Context:** Use with technology-forward leaders at incorporadoras or assessorias. SREI (Lei 14.382/2022) is creating a once-in-a-generation data opportunity.
**Supporting Data:** ARISP (SP) already operational; ONR expanding nationally. For the first time, matricula data, ownership chains, and onus records will be available digitally. Companies that build data infrastructure now will have 2--3 years of data advantage.
**Follow-up Question:** "Are you connected to SREI/ARISP yet? How do you currently access matricula information?"

## Objection Handling

| Objection | Response | Evidence |
|-----------|----------|----------|
| "Too expensive for our size" | The diagnostic is R$25K--R$75K -- less than 2 weeks of SPE reconciliation labor for a 20-SPE incorporadora. The first implementation (R$100K--R$250K) delivers 200--800% ROI in Year 1. | SPE labor costs of R$600K/year; AVM bad acquisition avoidance of R$400K--R$2M/year |
| "We already have Sienge/UAU" | Excellent ERP for construction. But Sienge doesn't aggregate ITBI data from 5 municipalities, doesn't parse editais, doesn't do ML valuation, and struggles with 25-SPE consolidation. We're the intelligence layer on top of your ERP. | Feature gap analysis vs. Sienge/UAU |
| "We subscribe to DataZAP" | DataZAP gives you listing data. We combine DataZAP + ITBI transactions + IBGE demographics + zoning data + cartorio records into an actionable pipeline integrated with your Sienge and Vista. Data without workflow integration is a dashboard you look at; we build systems that work. | Multi-source integration value |
| "We can build this in-house" | A data team costs R$400K+/year. Our land intelligence platform delivers in 10 weeks at R$200K with pre-built ITBI aggregation for multiple municipalities and proven zoning parsing. You'd need 6--9 months and municipality-specific expertise. | Time-to-value and cost comparison |
| "Our team knows the market" | Your team's knowledge is invaluable for judgment calls. We automate the 80% that's data work -- ITBI lookups, zoning checks, matricula reading -- so your experts spend time on the 20% that requires human expertise. | Augmentation not replacement framing |

## Discovery Call Framework

### Questions to Ask

1. "How many SPEs are you managing right now? Walk me through the monthly closing process."
2. "How do you source land acquisition opportunities? What data do you use?"
3. "How long does it take from identifying a land opportunity to making a purchase decision?"
4. "How do you value properties? Do you use ITBI data, FipeZAP, or just comparables?"
5. "How does your CRM data flow into your financial systems?"
6. "What's your current distrato rate? How do you forecast it?"
7. "For leilao: how many editais per batch? What's your screening process?"
8. "How do you access cartorio data today? Are you using SREI/ARISP?"
9. "What is your biggest data bottleneck right now?"
10. "How do you comply with LGPD for buyer personal data?"

### Red Flags (Disqualifiers)

- Revenue below R$30M (insufficient scale for meaningful ROI)
- Single active project (no SPE complexity pain)
- No ERP system (data foundation missing)
- Strong internal data team with executive mandate to build in-house
- No executive sponsorship -- purely IT-driven inquiry

### Green Flags (High-Fit Indicators)

- CFO expressing frustration with SPE reconciliation or audit findings
- Recently lost a land opportunity to a faster competitor
- Expanding to new cities without local market data
- Leilao assessoria experiencing volume growth beyond current screening capacity
- Recent audit finding on patrimonio de afetacao compliance
- Multiple SPEs with manual Excel consolidation
- Mentions "we need better data" in any context
- Interest in SREI/ARISP digital cartorio integration

## Pricing Strategy

| Engagement | Price | Value Anchor | ROI Multiple |
|-----------|-------|-------------|-------------|
| Diagnostic | R$25K--R$75K | Less than 2 weeks of manual SPE reconciliation labor | N/A (discovery) |
| Land Intelligence Platform | R$150K--R$300K | R$40--60M additional pipeline from faster land acquisition | 200x+ |
| Automated Valuation Engine | R$100K--R$250K | R$300K--R$1.8M/year in avoided bad acquisitions | 200--1,200% |
| SPE Financial Management | R$200K--R$400K | R$600K--R$1M/year in accounting labor + audit risk | 250--500% |
| Auction Intelligence | R$150K--R$350K | R$1.5M--R$7.5M/year in margin improvement | 400--3,000% |
| CRM Intelligence | R$80K--R$200K | 15--25% conversion improvement on existing pipeline | 1,250--3,125% |
| Monthly Retainer | R$10K--R$30K/mo | Ongoing data pipeline + model retraining + new municipalities | Maintenance |

## Proof Points

- **Portfolio projects**: florida-flip (market intelligence), leila-do-leilao (auction intelligence), incorporacoes-gestao (SPE management) -- live implementations demonstrating capability
- **Industry benchmarks**: Mid-market incorporadoras operate 4--8 disconnected systems; 60% use Excel for SPE consolidation; 90% do manual CMA valuation
- **Market urgency**: SREI rollout creating machine-readable property data for the first time; leilao volume up 40%+; MCMV 2M+ units in pipeline
- **Technology proof**: ITBI data aggregation across 5+ municipalities demonstrated; LLM-based edital parsing with 95%+ extraction accuracy; hedonic regression AVM with 8--12% variance
- **Regulatory drivers**: Patrimonio de afetacao increasingly mandatory; LGPD enforcement maturing; Lei 13.786/2018 distrato provisions creating financial modeling needs

## Competitive Positioning Statements

- vs. DataZAP/Hiperdados: "We build the pipeline that makes property data actionable in your workflow, not just a dashboard to look at."
- vs. Brain Inteligencia: "We deliver automated systems that run continuously, not one-time market studies that go stale."
- vs. Sienge/UAU: "We connect your ERP to ITBI data, FipeZAP, cartorios, and zoning databases -- the integrations no ERP offers."
- vs. In-house build: "We bring pre-built patterns from multiple real estate engagements. You get in 10 weeks what would take 6--9 months from scratch."
- vs. Big 4: "We deliver working systems at R$100K--R$400K, not slide decks at R$500K+."

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
