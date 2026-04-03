---
title: "Financial Services — Sales Playbook"
type: sales-playbook
vertical: financial-services
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [financial-services, sales, hooks, objection-handling, pricing, ICP]
---

# Financial Services — Sales Playbook

## Ideal Client Profile (ICP)

### Primary ICP: Fintech de Crédito (SCD/SEP)

| Attribute | Ideal | Acceptable | Disqualify |
|-----------|-------|------------|------------|
| Portfolio size | R$50M–R$500M | R$10M–R$50M | <R$10M (too small) or >R$1B (has in-house team) |
| Monthly applications | 200–1,000 | 100–200 | <50 (manual is fine) or >5,000 (needs platform, not consulting) |
| Engineering team | 2–5 developers | 1 developer | 0 (can't maintain) or 20+ (can build themselves) |
| Default rate | Above target (2–5%) | At target but wants to scale | Below 1% (not a pain point) |
| Funding stage | Series A / B | Seed (with revenue) | Pre-revenue |
| Decision cycle | 2–4 weeks | 4–8 weeks | >3 months (no urgency) |

### Secondary ICP: Factoring / FIDC

| Attribute | Ideal | Acceptable | Disqualify |
|-----------|-------|------------|------------|
| Portfolio size | R$50M–R$500M | R$5M–R$50M | <R$5M |
| Monthly operations | 50–500 | 20–50 | <20 |
| Engineering team | 0–2 (they outsource everything) | 2–5 | N/A |
| Credit analysis | Manual (Serasa score + gut feeling) | Semi-automated | Already has ML models |
| Government contract exposure | Yes (or interested) | Open to exploring | Exclusively consumer receivables |

### Tertiary ICP: Banco Digital Regional

| Attribute | Ideal | Acceptable | Disqualify |
|-----------|-------|------------|------------|
| Asset size | R$500M–R$5B | R$100M–R$500M | >R$10B (has budget for Big 4) |
| Credit products | Multiple (vehicle, payroll, SME) | Single product | No credit products |
| Engineering team | 5–15 | 3–5 | >30 |
| Key pain | Legacy system integration + Open Finance compliance | One or the other | "We're happy with our systems" |

## Sales Hooks

### Hook 1: "The 80/20 Credit Analyst Problem"

**Target:** CCO, Head of Risk
**Setup:** "How much time do your credit analysts spend collecting data vs. actually analyzing risk?"
**Insight:** "In every fintech we've assessed, analysts spend 80% of their time on data collection — querying bureaus, checking SCR, reviewing documents — and 20% on actual risk judgment. That ratio should be inverted."
**Offer:** "Our Credit Risk Intelligence Platform automates the 80%. Your analysts become risk decision-makers, not data clerks. One client went from 3 hours to 25 minutes per credit decision."
**Proof point:** Case Study 1 — 7.2x faster credit decisions, 31% NPL reduction

### Hook 2: "The Government Contract Goldmine"

**Target:** CEO, Commercial Director (especially factorings)
**Setup:** "Do you know which of your potential clients just won a R$5M government contract last week?"
**Insight:** "PNCP publishes thousands of contract awards daily. Every contractor who wins a government contract has predictable future cash flow — the ideal credit customer. Nobody in mid-market credit is systematically mining this data."
**Offer:** "We connect PNCP data to your credit origination pipeline. You see government contract awards within 48 hours, with the contractor already scored and a factoring proposal draft-ready."
**Proof point:** Case Study 3 — 5x increase in qualified leads, 44% portfolio growth, 62% lower default rate on PNCP-originated operations

### Hook 3: "Your Competitors Are Raising with AI Stories"

**Target:** CEO, Founder (Series A/B stage)
**Setup:** "What story are you telling investors about your data and AI capabilities?"
**Insight:** "Every fintech raising in 2026 needs an AI-native credit story. Investors are asking about proprietary scoring models, alternative data sources, and automated underwriting. Bureau-only scoring is table stakes."
**Offer:** "We build the AI-native credit infrastructure that makes your Series B story compelling — ML scoring, LLM credit memos, government contract data, Open Finance integration. Ready for investor demo in 3 months."
**Proof point:** Case Study 1 — client used LLM credit memo in Series B pitch

### Hook 4: "The R$X Per Credit Decision Problem"

**Target:** COO, Head of Operations
**Setup:** "Have you calculated your fully loaded cost per credit decision?"
**Insight:** "Most mid-market fintechs spend R$100–R$300 per credit decision when you include analyst time, bureau costs, overhead, and error-related rework. That number should be R$30–R$50. And it should be falling as you scale, not staying flat."
**Offer:** "Our diagnostic quantifies your cost per credit decision and identifies 50–75% reduction opportunities. Bureau cost optimization alone often saves R$200K–R$500K annually."
**Proof point:** Case Study 1 — 75% reduction in cost per credit decision; 52% reduction in bureau costs through intelligent routing

### Hook 5: "The Monthly SCR Crisis"

**Target:** Compliance Officer, Head of Operations
**Setup:** "How many person-hours does your team spend on SCR reporting every month?"
**Insight:** "We call it the 'SCR week' — the 3–5 days every month where your operations team drops everything to prepare, validate, and submit SCR files. Error rates of 3–5% are common, triggering BCB inquiries and correction cycles."
**Offer:** "SCR automation is included in every credit platform we build. One client went from 5% error rate to <0.1%, and the team got 3 days back every month."
**Proof point:** Case Study 1 — 98% reduction in SCR errors; eliminated monthly reporting crisis

## Objection Handling

### "We'll build it in-house"

**Response framework:**
1. **Acknowledge:** "That's a valid option if you have the right team."
2. **Quantify the alternative:** "An ML engineer costs R$25K–R$40K/month. A credit scoring platform needs 3–4 engineers for 6–12 months. That's R$600K–R$1.5M in salary alone, plus opportunity cost — those engineers aren't building product features."
3. **Time factor:** "We deliver a production system in 3–5 months. Internal builds typically take 9–18 months. How many months of suboptimal credit decisions is that worth?"
4. **Close:** "Most clients use us to build the first version, then maintain and iterate with their team. We transfer knowledge and code ownership."

### "We already use Serasa/ClearSale/Pluggy"

**Response framework:**
1. **Acknowledge:** "Good — those are solid tools for what they do."
2. **Reframe:** "Serasa gives you a bureau score. ClearSale gives you a fraud flag. Pluggy gives you data access. None of them build you a credit intelligence platform that combines all these inputs with ML scoring, LLM memos, government contract signals, and regulatory compliance. We're the integration and intelligence layer."
3. **Complementary positioning:** "We don't replace any of those — we make them more valuable by combining them into a unified decisioning system."

### "Our default rate is fine / we don't have a problem"

**Response framework:**
1. **Reframe from defense to offense:** "Great — then the question isn't reducing losses, it's scaling. Can you 3x your origination volume with the same team and the same default rate?"
2. **Hidden costs:** "What's your cost per credit decision? How many applications do you reject that a better model might approve? Every false negative is revenue you're leaving on the table."
3. **Future-proof:** "Your default rate is fine at R$80M. Will it stay fine at R$300M? The scoring methodology that works for 200 applications/month often breaks at 1,000."

### "Too expensive"

**Response framework:**
1. **Diagnostic as proof:** "Start with the diagnostic (R$25K–R$40K). We'll quantify the ROI with your data. If the numbers don't work, you've paid R$25K for a comprehensive operations audit — still valuable."
2. **ROI reframe:** "Our average client sees 4–5x ROI in Year 1. R$200K invested returns R$800K–R$1M in savings and new revenue. The question isn't whether you can afford it — it's whether you can afford not to."
3. **Phase the engagement:** "We can start with the highest-ROI project (often bureau cost optimization or PNCP credit origination) and fund the next phase from savings."

### "We need to check with our investors / board"

**Response framework:**
1. **Enable the internal sell:** "Happy to prepare a one-pager for your board with the ROI model from our diagnostic. Most boards love this story — it's exactly the AI-native narrative they want to see."
2. **Investor angle:** "We've seen investor conversations accelerate when the fintech can demo ML credit scoring and LLM memos. This often becomes a fundraising asset, not just an operating expense."
3. **Timeline pressure:** "When is your next board meeting? We can have diagnostic results ready by then."

### "Data privacy / LGPD concerns"

**Response framework:**
1. **Address directly:** "LGPD compliance is built into everything we build. Consent management, purpose limitation, data minimization, encryption, access controls, audit trails."
2. **Regulatory expertise:** "We build RAG-powered compliance engines that keep your team current on BCB and ANPD requirements. Compliance isn't a risk of working with us — it's a deliverable."
3. **Reference:** "We include LGPD compliance assessment in every diagnostic. If there are gaps, we identify them. Most clients find our engagement improves their compliance posture."

## Outbound Prospecting Strategy

### Channel 1: ABFintechs and ANFAC Events

- Attend ABFintechs annual summit, ANFAC conferences, and regional fintech meetups
- Target: 2–3 events per quarter
- Goal: 5–10 qualified conversations per event
- Follow-up: Diagnostic offer within 48 hours

### Channel 2: LinkedIn Content + Outbound

- Publish weekly content on credit intelligence, Open Finance, government contract data
- Target decision-makers at ICP companies
- Message sequence: insight → case study → diagnostic offer
- Goal: 3–5 discovery calls per month from LinkedIn

### Channel 3: Referral Network

- BaaS providers (QI Tech, Dock, Zoop) — they serve fintechs but don't offer credit intelligence
- Law firms specializing in fintech regulation — they advise clients who need our services
- VCs investing in fintech — portfolio companies need AI infrastructure for next round narrative
- Accounting firms serving factorings — they see the operational pain firsthand

### Channel 4: PNCP Intelligence as Lead Magnet

- Use licitaleads data to identify companies winning large government contracts
- Cross-reference with factorings in the same region/sector
- Outbound to factoring: "Company X just won a R$10M government contract in your territory. Here's how you can be the first to offer factoring."
- Demonstrates capability while generating leads

## Pricing Strategy

### Diagnostic Pricing

| Client Type | Price | Justification |
|-------------|-------|---------------|
| Fintech de crédito | R$30K–R$60K | Full scope: credit ops, data, compliance, tech assessment |
| Factoring/FIDC | R$20K–R$40K | Lighter scope: credit ops, data audit, PNCP opportunity sizing |
| Banco digital | R$40K–R$60K | Full scope + legacy system assessment |
| Correspondente bancário | R$20K–R$30K | Operations + compliance focus |

### Implementation Pricing

| Project | Price Range | Value Anchor |
|---------|------------|--------------|
| Credit Risk Intelligence Platform | R$150K–R$350K | "Replaces 2–3 analyst FTEs (R$500K+/year) and reduces NPL by 15–30%" |
| Government Contract Credit Origination | R$100K–R$250K | "Generates R$500K–R$1M in new annual revenue from PNCP-originated operations" |
| Automated Collateral Valuation | R$80K–R$200K | "Eliminates R$500–R$2K per manual appraisal; reduces collateral shortfall by 10–15%" |
| Open Finance Data Integration | R$100K–R$250K | "Enables cash-flow-based lending — new product line; 20–40% scoring improvement" |
| Fraud Detection Engine | R$150K–R$400K | "Prevents R$2M–R$10M in annual fraud losses; 40–60% fraud reduction" |

### Discount Policy

- **Multi-project discount:** 10–15% for 2+ projects committed upfront
- **Diagnostic credit:** 100% of diagnostic fee applied to implementation if signed within 30 days
- **Pilot pricing:** First project at 80% for "design partner" clients willing to provide case study testimonial
- **Never discount below:** R$80K for implementation (below this, unit economics don't work)

## Sales Cycle Benchmarks

| Stage | Duration | Conversion Rate | Key Action |
|-------|----------|----------------|------------|
| Discovery call → Diagnostic proposal | 1–2 weeks | 40% | Send ROI estimate based on publicly available data |
| Diagnostic proposal → Signed | 1–3 weeks | 60% | Reference case study; offer diagnostic credit toward implementation |
| Diagnostic → Implementation proposal | 1–2 weeks (during diagnostic delivery) | 80% | Quantified ROI in diagnostic report makes this near-automatic |
| Implementation proposal → Signed | 2–4 weeks | 50% | Board/investor alignment; phase the engagement if budget constrained |
| **Total: First contact → Implementation start** | **6–12 weeks** | **~10% of qualified leads** | |

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
