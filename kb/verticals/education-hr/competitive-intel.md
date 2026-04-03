---
title: "Education & HR — Competitive Intelligence"
type: competitive-intel
vertical: education-hr
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [education-hr, competitors, pricing, positioning, gupy, kenoby, revelo]
---

# Education & HR — Competitive Intelligence

## Competitive Landscape Overview

The Education & HR AI space in Brazil has one dominant player (Gupy) and a fragmented field of mid-market competitors. Critically, most competitors are **product companies** building monolithic platforms — not consulting/infrastructure partners. JP Ventures competes in a different layer: we build the AI data infrastructure that mid-market players need to compete with Gupy, rather than competing with Gupy directly.

## Competitor Profiles

### Tier 1: Market Leaders (Benchmarks, Not Targets)

#### Gupy
- **What they do**: End-to-end recruitment platform with AI screening, chatbot, video interviews, ATS
- **Founded**: 2015 | **HQ**: São Paulo | **Employees**: 800+
- **Funding**: R$500M+ total (Series C+)
- **Revenue estimate**: R$200M+ ARR
- **AI capabilities**: Proprietary AI screening (Gaia), chatbot for candidate engagement, predictive analytics for hiring
- **Strengths**: Market dominance (~40% of Brazilian ATS market), massive training data (millions of hiring decisions), strong brand, integrated platform
- **Weaknesses**: Enterprise-focused pricing excludes smaller companies, monolithic platform limits customization, AI is a black box (low explainability), slow to adapt to GenAI wave
- **Relevance to us**: Gupy is the benchmark our clients compare against. Our job is to give mid-market ATS platforms "Gupy-level AI" at a fraction of the cost. Gupy's rigidity is our advantage — we build flexible, modular solutions.

#### Catho / InfoJobs (Seek Group)
- **What they do**: Job boards with candidate databases, basic matching
- **Revenue estimate**: R$100M+ combined
- **AI capabilities**: Basic keyword matching, recommendation algorithms, resume parsing (limited)
- **Strengths**: Massive candidate databases (20M+ profiles on Catho), brand recognition, Indeed/Seek backing
- **Weaknesses**: Legacy technology, poor AI capabilities, losing market share to Gupy and LinkedIn
- **Relevance to us**: Their candidate data is valuable but underutilized. Mid-market companies posting on these boards need better matching tools.

### Tier 2: Mid-Market Competitors (Direct Competition Zone)

#### Kenoby
- **What they do**: ATS platform for mid-market companies
- **Revenue estimate**: R$30-50M
- **AI capabilities**: Basic screening automation, cultural fit assessment, integration marketplace
- **Strengths**: Strong mid-market positioning, good UX, integration ecosystem
- **Weaknesses**: AI is rudimentary (keyword-based), potentially being acquired by Gupy (would remove from market)
- **Pricing**: Platform SaaS R$2K-R$15K/mo depending on company size
- **Relevance to us**: Kenoby clients are prime prospects for our ATS Screening API — they need better matching but cannot build AI in-house.

#### Revelo
- **What they do**: Reverse recruitment marketplace for tech talent — companies apply to candidates
- **Revenue estimate**: R$20-40M
- **AI capabilities**: Matching algorithm (skill-based), salary prediction, candidate scoring
- **Strengths**: Innovative model (reverse recruiting), strong tech talent pool, good matching for developer roles
- **Weaknesses**: Narrow focus (tech talent only), matching algorithm struggles outside core competencies, limited to São Paulo/remote
- **Pricing**: Success fee model (15-25% of annual salary) + platform subscription
- **Relevance to us**: Their matching challenges outside tech roles are exactly what our Skills Taxonomy + Semantic Matching patterns solve.

#### ABLER
- **What they do**: ATS platform focused on simplicity for SMBs and mid-market
- **Revenue estimate**: R$10-20M
- **Employees**: 50-100
- **AI capabilities**: Low — basic automation, no AI matching
- **Strengths**: Simple UX, affordable pricing, growing user base
- **Weaknesses**: No AI capabilities, will lose clients as AI expectations rise
- **Pricing**: R$500-R$5K/mo
- **Relevance to us**: **Strong prospect** — they need AI capabilities urgently to compete and lack the team to build internally. Perfect fit for our ATS Screening API.

#### Bettha
- **What they do**: Career development platform for young professionals — assessments, matching, career guidance
- **Revenue estimate**: R$5-15M
- **AI capabilities**: Behavioral assessments, basic profile matching
- **Strengths**: Good positioning with young professionals, gamified assessments, employer brand partnerships
- **Weaknesses**: Assessment methodology is proprietary but not AI-native, limited job market data integration
- **Relevance to us**: **Good prospect** for Employability Assessment Module — they could enhance their platform with real job market data integration.

### Tier 3: Adjacent Players

#### Talent Academy
- **Focus**: People analytics and development platform
- **AI capabilities**: Behavioral analysis, team composition optimization
- **Relevance**: Competes in the Skills Gap Analytics space; their product approach differs from our infrastructure approach

#### Mindsight
- **Focus**: People analytics, psychometric assessments
- **AI capabilities**: Psychometric modeling, predictive analytics for hiring
- **Relevance**: Strong in assessment science but weak in data infrastructure — could be partner or client

#### Rankdone
- **Focus**: Technical skills testing for recruitment
- **AI capabilities**: Automated test generation and scoring
- **Relevance**: Adjacent to our ATS Screening API; technical assessment is one signal in our matching model

#### Taqe
- **Focus**: High-volume recruitment automation
- **AI capabilities**: Chatbot-driven screening, basic matching for operational roles
- **Relevance**: High-volume segment where our CV Intelligence Platform + ATS API create the most throughput improvement

## Competitive Positioning Matrix

| Capability | Gupy | Kenoby | Revelo | ABLER | JP Ventures |
|-----------|------|--------|--------|-------|-------------|
| AI-powered CV parsing | Strong (proprietary) | Weak | Medium | None | Strong (cv10x-based) |
| Semantic job matching | Strong | Weak (keyword) | Medium (tech focus) | None | Strong (embeddings + taxonomy) |
| Skills taxonomy | Proprietary | None | Limited (tech only) | None | CBO-based + custom |
| Bias auditing | Unknown | None | None | None | Built-in (LGPD compliant) |
| Explainability | Low (black box) | N/A | Low | N/A | High (SHAP/LIME + NL explanations) |
| Public data integration | None visible | None | None | None | RAIS/CAGED/CBO/INEP |
| Customization | Low (platform lock-in) | Medium | Low | Low | High (modular API) |
| Mid-market pricing | Expensive (R$5K-R$20K/mo) | Moderate | Success fee | Affordable | Project + retainer |

## Pricing Intelligence

### Market Pricing Ranges

| Service Type | Low | Mid | High | Notes |
|-------------|-----|-----|------|-------|
| ATS platform subscription | R$500/mo | R$5K/mo | R$20K/mo | Scales with company size and features |
| AI screening add-on | R$1K/mo | R$3K/mo | R$10K/mo | Premium feature on top of ATS |
| Recruitment marketplace (success fee) | 10% annual salary | 18% | 25% | Higher for scarce skills |
| HR analytics platform | R$2K/mo | R$8K/mo | R$25K/mo | Enterprise pricing can go higher |
| Custom AI implementation | R$50K project | R$150K | R$400K+ | Where JP Ventures operates |
| Ongoing AI infrastructure retainer | R$8K/mo | R$18K/mo | R$35K/mo | Where JP Ventures operates |

### JP Ventures Pricing vs. Build-In-House

| Component | JP Ventures (Project) | In-House (Annual Cost) | JP Ventures Advantage |
|-----------|---------------------|----------------------|----------------------|
| CV Intelligence Platform | R$60K-R$150K (one-time) | R$600K+ (2 ML engineers x R$25K/mo x 12) | 75%+ cost savings; delivered in 8-12 weeks vs. 12+ months |
| ATS Screening API | R$100K-R$250K (one-time) | R$900K+ (3 engineers x 12 months) | 70%+ cost savings; production-tested patterns |
| Employability Assessment | R$80K-R$200K (one-time) | R$500K+ (2 engineers x 12 months) | 60%+ cost savings; includes public data integration |

## Competitive Threats

| Threat | Probability | Impact | Our Response |
|--------|------------|--------|-------------|
| Gupy launches mid-market tier | Medium | High — could eat our prospect pool | We offer customization Gupy cannot; modular > monolithic |
| OpenAI/Google launch HR-specific AI tools | Medium | Medium — commoditizes basic CV parsing | We integrate any LLM; our value is data infrastructure + domain expertise, not the model |
| Brazilian HR tech startup raises large round | Medium | Low-Medium — one more competitor | We are infrastructure partners, not platform competitors |
| Client builds AI team after our engagement | Low-Medium | Medium — lose retainer | Retainer value > hiring cost; we evolve faster than internal teams |
| International HR AI platforms enter Brazil | Low | Medium — language/regulatory barrier protects short-term | Portuguese NLP + LGPD expertise + CBO/RAIS integration are hard to replicate |

## Win/Loss Analysis Framework

Track for every engagement:

| Factor | Question | Scoring |
|--------|----------|---------|
| Technical fit | Did our solution architecture match client needs? | 1-5 |
| Pricing | Was our price competitive vs. alternatives? | 1-5 |
| Domain credibility | Did cv10x and prior work convince them we understand HR/Ed? | 1-5 |
| Speed to value | Did our timeline beat build-in-house or competitor offers? | 1-5 |
| Champion strength | Did we have an internal champion with budget authority? | 1-5 |
| Competitive pressure | Was there a competing proposal? From whom? | Detail |

## Strategic Implications

1. **We are not competing with Gupy** — we are enabling Gupy's competitors. This positioning avoids the largest player and serves a hungry mid-market.
2. **AI explainability is a differentiator now, a requirement soon** — PL 2338/2023 will likely mandate it. Building it now creates competitive moat.
3. **Public data integration (RAIS/CBO/CAGED) is our unique angle** — no competitor systematically leverages these sources. This is domain infrastructure that product companies overlook.
4. **cv10x gives us production credibility** — we are not theorists; we have working CV intelligence code. This closes deals.
5. **Modular beats monolithic for mid-market** — mid-market companies want to enhance their existing tools, not replace them. API-first architecture wins.

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
