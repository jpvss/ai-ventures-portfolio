---
title: "Automotive — Sales Playbook"
type: sales-playbook
vertical: automotive
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [automotive, sales, hooks, objections, pricing, dealers, consignment]
---

# Automotive — Sales Playbook

## Ideal Client Profile (ICP)

| Attribute | Criteria |
|-----------|---------|
| Company Type | Multi-brand dealership (concessionária multimarca), consignment platform (plataforma de consignação), or premium reseller (revenda premium) |
| Annual Revenue | R$5M–R$100M |
| Inventory Size | 50–500 vehicles in stock (dealers) or 20–150 under mandate (consignment) |
| Technology Maturity | FIPE-only pricing, spreadsheet/basic DMS inventory management, manual marketplace listings, no systematic lead management |
| Pain Indicators | High days-on-lot (>60 days average), vehicles sold at loss (>5% of transactions), no floor plan cost visibility, losing mandates/inventory to faster competitors |
| Decision Maker | Owner/Director (concessionária), Founder/CEO (platform), Sales Director |
| Budget Holder | Owner/Director directly (mid-market dealers are owner-operated) |

### Secondary ICP: Vehicle-Backed Fintechs

| Attribute | Criteria |
|-----------|---------|
| Company Type | Fintech offering CDC auto, vehicle refinancing, consórcio |
| Loan Portfolio | R$50M–R$500M+ |
| Pain Indicators | Collateral recovery below model expectations, FIPE-only LTV calculations, regulatory pressure on valuation methodology |
| Decision Maker | Head of Credit/Risk, CTO |
| Entry Project | Vehicle Credit Risk Scoring (R$100K–R$250K) |

## Sales Hooks

### Hook 1: "Every car on your lot costs R$1,500/month just sitting there."

**Context:** Use when the prospect has visible inventory aging problems or when SELIC is high (>10%). Floor plan financing is the most tangible, quantifiable pain for dealers.

**Supporting Data:** At SELIC ~13.25%, floor plan financing costs R$500–R$2,000 per vehicle per month depending on vehicle value and financing terms. A 200-vehicle lot with 72-day average turnover is paying R$300K+/month in carrying costs. Reducing average days-on-lot from 72 to 48 saves R$100K/month — R$1.2M/year. Our Inventory Intelligence Dashboard shows every vehicle's carrying cost in real time.

**Follow-up Question:** "What is your average days-on-lot right now? How many vehicles in your stock are over 60 days? Do you know what those cars have cost you in floor plan interest?"

### Hook 2: "FIPE says the same price for a 30K km car and a 120K km car. Your margin lives in the gap."

**Context:** Use when the prospect uses FIPE as primary pricing reference. This hook targets the fundamental data limitation that affects every transaction.

**Supporting Data:** FIPE publishes one monthly price per make/model/year — no regional, condition, mileage, or color adjustment. Real market prices vary 10–30% based on these factors. A dealer buying at "85% of FIPE" is profitable on a low-km, good-condition car but underwater on a high-km beater — both priced the same by FIPE. Our Valuation Engine adds 10+ factors on top of FIPE to capture these spreads.

**Follow-up Question:** "Walk me through how you price an acquisition. When a car comes in, what data do you look at? How do you adjust for condition and mileage?"

### Hook 3: "Your competitors already have real-time marketplace data. You're pricing blind."

**Context:** Use when the prospect competes against digital-first platforms (InstaCarro, Volanty) or larger dealer groups. Creates competitive urgency.

**Supporting Data:** InstaCarro provides instant offers based on real-time data. Webmotors has 500K+ active listings that show exactly what the market is charging. Consumers compare prices on OLX before walking into a dealership. If your listing is 10% above the marketplace median, buyers never walk in. Our system monitors marketplace comparables for every vehicle in your stock and alerts you when you're overpriced.

**Follow-up Question:** "How do you monitor competitor pricing on OLX and Webmotors? How often do you update your listing prices? When was the last time you adjusted a price based on marketplace data?"

### Hook 4: "Show car owners the math, and they'll consign with you instead of selling to the competitor."

**Context:** Use specifically with consignment platforms. The deixacomigo model proves this approach works.

**Supporting Data:** Car owners typically sell to dealers at 75–85% of FIPE because they don't see the consignment alternative quantified. Our valuation tool shows: "Dealer offer: R$68K. Consignment net (after 5% commission): R$82K. You keep R$14K more." This specific, data-backed comparison converts 12% of valuations into consignment mandates. We've deployed this for platforms generating R$120K–R$200K/month in new commission revenue.

**Follow-up Question:** "How do you currently pitch consignment value to car owners? Do you have data showing them the specific financial benefit? What's your lead-to-mandate conversion rate?"

### Hook 5: "Your FIPE-only LTV model has a 15–25% blind spot. When borrowers default, you're recovering less than you planned."

**Context:** Use with vehicle-backed fintechs. Targets the credit risk / collateral valuation pain.

**Supporting Data:** FIPE is a retail reference; forced-sale recovery at auction is typically 15–25% below FIPE. A fintech setting LTV at 70% of FIPE assumes recovery at 70% × FIPE, but actual auction recovery averages 62% of FIPE — meaning effective LTV is 112% (underwater). Our collateral valuation model predicts forced-sale value with 91% accuracy, reducing collateral-related losses by 73%.

**Follow-up Question:** "What is your current collateral valuation methodology? What's your average recovery rate when you repossess and auction a vehicle? How does that compare to your LTV assumptions?"

## Objection Handling

| Objection | Response | Evidence |
|-----------|----------|----------|
| "I know my market — I've been doing this for 20 years" | "Your experience is the foundation — our model codifies it and extends it with data you can't track manually: 500K+ marketplace listings, regional demand shifts, and competitor pricing changes daily." | Case 1: dealer who priced by gut had 8% loss rate, reduced to 3% with model |
| "FIPE is good enough" | "FIPE is good for a starting point. But the same Civic 2022 is worth R$8K more in SP interior than in Recife. At 120K km vs. 30K km, the real gap is R$12K. FIPE shows one number for both." | Regional and condition price spread analysis |
| "Too expensive for my operation" | "Let's do the math: 200 cars × R$1,200/month floor plan × 24 extra days on average = R$192K/year in unnecessary carrying costs. Our R$100K project pays for itself in 6 months." | Floor plan cost calculation; Case 1 ROI |
| "I can check OLX/Webmotors myself" | "You can — for one car at a time, manually. We do it for every car in your stock, every day, automatically. And we show you competitive positioning + recommended pricing, not just raw data." | Dashboard demo showing per-vehicle market positioning |
| "My guys are good evaluators" | "They probably are — for the cars they see regularly. But how consistent are they? Does evaluator A and evaluator B grade the same car identically? Standardized scoring + photo AI creates consistency." | Condition scoring variance analysis |
| "We tried software before and it didn't work" | "Most automotive software is generic DMS. We build AI specifically for your pricing and inventory decisions, integrated with your existing process — not a rip-and-replace." | deixacomigo as proof of automotive-specific tooling |

## Discovery Call Framework

### Questions to Ask

1. Walk me through how you buy a vehicle. What data do you look at? Who makes the final decision?
2. What is your average gross margin per vehicle? Has it changed in the last 2 years?
3. How many vehicles do you have in stock right now? How many are over 60 days? Over 90 days?
4. What is your floor plan financing cost per month? Do you know your carrying cost per vehicle per day?
5. How do you decide when to reduce the price on a vehicle that isn't selling?
6. Do you list on OLX, Webmotors, or other marketplaces? How are listings created? How often are prices updated?
7. How do you evaluate vehicle condition? Is the process documented? How consistent is it across your team?
8. What percentage of your sales include financing or insurance? Do you track attach rates?
9. How do you generate leads online? What's your response time to an online inquiry?
10. What's your biggest frustration with running the business today?

### Red Flags (Disqualifiers)

- Fewer than 30 vehicles in stock (economics don't justify investment)
- Owner resistant to data-driven approaches — "I price by feeling and it works"
- Currently in financial distress (can't fund even a diagnostic)
- Unwilling to share transaction data during diagnostic
- Expects fully autonomous pricing with zero human oversight (mismatched expectations)

### Green Flags (High-Fit Indicators)

- Owner can quantify a specific pricing mistake — "I lost R$15K on that Hilux last month"
- High floor plan costs and awareness that carrying costs are a problem
- Growing operation (more locations, more stock) and recognizing that current process doesn't scale
- Has lost mandates or inventory to digital-first competitors
- Already uses OLX/Webmotors and understands marketplace dynamics
- Interested in ancillary revenue (insurance, financing attach rates)
- Open to sharing data and willing to run a paid diagnostic

## Pricing Strategy

| Engagement | Price | Value Anchor | ROI Multiple |
|-----------|-------|-------------|-------------|
| Diagnostic | R$15K–R$40K | Identifies R$200K–R$1M+ in annual margin leakage | 5–25x |
| 1st Implementation (Valuation Engine) | R$80K–R$200K | R$300K–R$1.2M in annual carrying cost savings + margin improvement | 2–6x Year 1 |
| White-label deixacomigo | R$20K–R$40K + R$3K–R$8K/mo | R$120K–R$200K/month in new commission revenue (consignment) | 3–5x Year 1 |
| Full 12-Month Portfolio | R$500K–R$1.5M | R$1M–R$5M+ in combined value (margin improvement + carrying cost savings + new revenue) | 2–5x |
| Monthly Retainer | R$10K–R$30K/month | Continuous pricing accuracy, scraper maintenance, model retraining | Ongoing value protection |

## Proof Points

- **Days-on-lot reduction**: 72 → 48 days (33% improvement)
- **Floor plan savings**: R$100K/month on a 250-vehicle lot
- **Loss sale reduction**: 8% → 3% of transactions
- **Gross margin improvement**: R$4,200 → R$5,800 per vehicle (38%)
- **Lead cost (valuation tool)**: R$15 vs. R$80–R$150 for paid ads
- **Valuation-to-mandate conversion**: 12% (consignment)
- **Collateral loss reduction**: 73% (fintech)
- **White-label deployment**: 3 weeks to live
- **FIPE API response**: <3 seconds with cache (deixacomigo)
- **deixacomigo**: Live product at deixacomigo.app demonstrating the approach

## Competitive Positioning Statements

- **vs. Kavak / heavy platforms**: "Kavak burned R$1B trying to buy and sell cars. We build the intelligence layer so you can buy and sell smarter — without the R$1B."
- **vs. InstaCarro**: "InstaCarro helps sellers leave your lot. We help you know which cars to buy and at what price, so sellers come to your lot."
- **vs. spreadsheets / gut feeling**: "Your gut is right 80% of the time. The 20% where it's wrong costs you R$500K+/year. We make the 80% faster and fix the 20%."
- **vs. generic DMS vendors**: "Your DMS tracks what happened. We predict what's going to happen — which cars will sell, at what price, and how fast."

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
