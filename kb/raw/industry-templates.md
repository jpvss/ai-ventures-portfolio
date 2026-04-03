# AI-native agency engagement templates for Brazilian mid-market verticals

**Four industry-specific playbooks — mining, investment advisory, insurance/surety bonds, and auctions — form the foundation for a productized AI data infrastructure consulting business in Brazil.** Each vertical reveals a distinct pattern: fragmented data systems, manual compliance workflows, and regulatory complexity create acute pain for mid-market companies that lack the resources of industry giants. The opportunity is significant — Brazil's mid-market across these four verticals represents hundreds of billions of reais in revenue, yet most firms operate with spreadsheets, disconnected legacy systems, and manual processes. The AI consulting engagement model follows a consistent arc: a paid diagnostic (R$25K–R$75K) surfaces quantified waste, followed by implementation projects (R$80K–R$1M each) that deliver 3–10x ROI within 12 months.

---

## VERTICAL 1: Mining consulting (Consultoria de Mineração)

### The data maturity gap in Brazilian mining

Mid-market Brazilian miners (R$100M–R$2B revenue) typically operate with **5–8 disconnected systems** that don't communicate. TOTVS Protheus dominates ERP (~60% penetration), while mine planning lives in GEOVIA Surpac, Deswik, or Vulcan. Fleet management runs on Modular DISPATCH, Cat MineStar, or Hexagon Jigsaw. Environmental monitoring sits in standalone spreadsheets. Lab data lives in LIMS. Financial data stays in the ERP. The result: geological models never flow automatically to production systems, CFEM royalty calculations happen in Excel, and environmental license compliance is tracked manually.

Brazil's mineral sector generated **R$248.2B in revenue in 2023**, with CFEM royalty collection reaching **R$7.4B in 2024**. IBRAM projects **US$64.5B in mining investments from 2024–2028**. The global digital mining market is growing at 9.8% CAGR to reach $18.1B by 2030. Yet mid-market miners use only 30–40% of their fleet management system capabilities, and most compliance reporting remains manual.

Real examples of adoption are emerging: Nexa Resources implemented Databricks for AI-driven operational insights. CBA (Companhia Brasileira de Alumínio) deployed AI-powered water treatment at its Miraí plant, reducing chemical usage by 80%. Vale's autonomous trucks at Brucutu achieved 11% productivity gains with zero accidents. The Mining Hub in Belo Horizonte connects 22+ mining companies with innovation providers, and BNDES has a R$1B fund targeting mining companies under R$300M revenue.

### Diagnostic engagement template (R$25K–R$75K, 3–4 weeks)

**Week 1 — Data landscape and systems audit.** Inventory all IT systems: ERP (TOTVS Protheus or SAP Business One), mine planning (Surpac/Deswik/Vulcan/Datamine), fleet management (DISPATCH/MineStar/Wenco/Hexagon), environmental monitoring, and lab/LIMS. Map data flows between geology, mine planning, production, sales, and finance. Identify siloed databases and evaluate ANM compliance systems including RAL submission workflow, CFEM calculation process, and SIGMINE/Cadastro Mineiro usage.

**Week 2 — Process and compliance assessment.** Review all reporting workflows: ANM (RAL, CFEM/DIEF, DIPEM), environmental (IBAMA/SEMAD condicionantes, PRAD updates), safety (NR-22 PGR, CIPAMIN records, incident logs). Assess CFEM calculation — most mid-market miners use spreadsheets to calculate CFEM based on receita bruta minus ICMS/PIS/COFINS with aliquots of 1%–3.5%. Evaluate environmental license compliance tracking for LP/LI/LO condicionantes and monitoring deadlines. Review dam safety compliance under Lei 14.066/2020, which mandates PAE for all mining tailings dams.

**Week 3 — Operational efficiency analysis.** Evaluate FMS utilization rates, ore grade reconciliation processes (typically manual mine-to-mill), maintenance management (preventive vs. predictive), energy consumption monitoring, and water balance/outorga compliance.

**Week 4 — Report and roadmap delivery.** Deliver Data Maturity Scorecard (1–5 scale across 8 dimensions: data integration, reporting automation, compliance digitization, operational analytics, ESG readiness, safety analytics, geological data management, financial/CFEM automation), current-state architecture diagram, gap analysis, top 5 prioritized opportunities with ROI projections, and a 12-month implementation roadmap.

### Implementation playbook

**Project 1: Automated CFEM and ANM compliance engine** (R$150K–R$350K, 8–12 weeks). Integrates TOTVS Protheus sales data with ANM's PGRM platform (launched March 2025 by Serpro) for automated CFEM calculation and DIEF digital submission. Applies substance-specific aliquots (iron ore 3.5%, gold 1.5%, bauxite/manganese/niobium 3%, diamonds 2%) with proper tax deductions. Auto-generates RAL data from production systems. ROI: eliminates 40–80 hours/month of manual calculation, recovers R$560K–R$1.4M annually in overpayment corrections, avoids 30% surcharge penalties on underpayments.

**Project 2: Environmental compliance dashboard and alert system** (R$200K–R$500K, 10–14 weeks). Centralized tracker for all environmental license condicionantes (LP/LI/LO), PRAD milestones, water monitoring (outorga), dam safety indicators under Lei 14.066/2020, and air/noise quality. Automated alerts for upcoming deadlines. Integrates with SEMAD's SLA system (Minas Gerais) and IBAMA's Portal Ecossistemas. ROI: prevents license suspension (operational halt costs R$500K–R$5M per day), reduces consulting fees by 50%, avoids fines under Lei 9.605/98 (R$50 to R$50M).

**Project 3: Fleet and production analytics platform** (R$300K–R$700K, 12–16 weeks). Data integration layer connecting FMS with mine planning software and ERP. Real-time dashboards for truck cycle times, equipment utilization, shovel productivity, and grade reconciliation. Predictive models for equipment failure. ROI: **5–15% improvement in fleet productivity**, 10–20% reduction in unplanned downtime. For a 30-truck operation, this translates to R$10–25M/year in additional value.

**Project 4: ESG reporting and safety intelligence platform** (R$250K–R$500K, 12–16 weeks). Automated ESG data collection across GRI/SASB/ISSB standards. NR-22 compliance tracker including PGR management, incident tracking, CIPAMIN records, and training completion. Carbon emissions calculator (Scope 1, 2, 3). ROI: reduces ESG report preparation from months to weeks, improves access to ESG-linked financing.

**Project 5: Geological data integration and AI-assisted grade optimization** (R$400K–R$1M, 16–24 weeks). Unified geological data platform connecting drilling data, assay results, block models, and production data. ML models for ore grade prediction and blending optimization. ROI: 2–5% improvement in head grade through better blending, significant reduction in ore dilution.

### Reusable solution patterns

- **Automated CFEM calculation engine**: NF-e data extraction → substance-specific aliquots → tax deduction logic → DIEF-CFEM submission → PGRM reconciliation
- **Environmental condicionante tracker**: License document parsing → deadline/requirement extraction → monitoring calendar → alert triggers → compliance evidence packages
- **Predictive maintenance dashboard**: OEM telemetry (Cat Product Link, Komatsu KOMTRAX) + FMS data → ML anomaly detection → failure prediction → scheduled maintenance → cost avoidance calculation
- **Fleet optimization engine**: FMS real-time data → truck dispatch/routing optimization → queue minimization → payload maximization → fuel reduction
- **Dam safety monitoring platform**: Instrumentation data aggregation (piezometers, inclinometers) → real-time visualization → anomaly detection → automated stability reports → Lei 14.066/2020 compliance
- **AI-powered ore blending optimizer**: Block model grade data + stockpile inventory + quality constraints → optimal blending plans
- **NR-22 safety intelligence**: Incident data + near-miss reports + training records → high-risk prediction → PGR updates → CIPAMIN agenda management
- **RAL auto-generator**: Production database + geological data + sales records → auto-populated RAL submission fields → data validation → ANM digital submission

### Quantified client outcome examples

**CFEM compliance automation** for a mid-market iron ore miner with R$800M revenue and 3.5% CFEM rate (~R$28M annual). Manual calculation errors of 2–5% result in R$560K–R$1.4M in annual overpayments or devastating 30% surcharges on underpayments. Staff time savings of 960 hours/year. **ROI: 400–800% in Year 1.**

**Fleet productivity optimization** for a 30-truck open-pit operation at 75% utilization. A 5–10% utilization increase delivers R$10–25M/year against a R$300–700K investment. **ROI: 1,400–3,500%.**

**Environmental license protection**: one prevented 30-day suspension avoids R$15–150M in halted-operation impact. Investment of R$200–500K pays for itself 30–300x over.

**Predictive maintenance** for a 50-unit heavy equipment fleet with R$50–200K cost per unplanned event and 15–25 events/year. 30–50% reduction in unplanned events yields **R$225K–R$2.5M in annual savings**.

### Regulatory and compliance map

| Agency/Law | Scope | Key Requirements | Digital Systems |
|---|---|---|---|
| **ANM** | Mining rights, royalties, dam safety | CFEM monthly payment, RAL annual report, DIPEM, dam monitoring | PGRM (March 2025), SIGMINE Portal, Cadastro Mineiro, DIEF-CFEM |
| **IBAMA** | Federal environmental licensing | EIA/RIMA, LP/LI/LO for federal-scope projects | Portal Ecossistemas |
| **SEMAD/COPAM (MG)** | State environmental licensing | LP/LI/LO, AAF (classes 1-2), monitoring reports | SLA system (since 2019) |
| **Lei 14.066/2020** | Dam safety (PNSB) | PAE mandatory for ALL mining tailings dams, stability declarations, real-time data to ANM | SNISB |
| **Lei 13.540/2017** | CFEM reform | Aliquots 1%–3.5% on receita bruta minus taxes, monthly payment | ANM CFEM portal |
| **NR-22 (updated May 2024)** | Mining safety and health | PGR, CIPAMIN, SIPATMIN, training requirements, incident reporting | Mostly manual |

CFEM aliquots: iron ore 3.5%, gold 1.5%, bauxite/manganese/niobium 3%, diamonds 2%, other metallic 2%, construction materials 1%, fertilizers 0.2%.

### Technical patterns and integration points

**Typical mid-market miner's systems landscape**: TOTVS Protheus (REST APIs, Smart Analytics), GEOVIA Surpac or Deswik for mine planning, Modular DISPATCH or Cat MineStar for fleet management, standalone environmental sensors, separate lab/LIMS systems. Most FMS expose data via SQL databases, REST APIs, or OPC-UA.

**Key APIs and data sources**: ANM SIGMINE (shapefiles/KMZ downloads, new ArcGIS web APIs), ANM PGRM for CFEM/DIEF submission, TOTVS Protheus REST API framework, Cat Product Link and Komatsu KOMTRAX telemetry APIs, Jazida.com (commercial ANM data integration platform), IBGE/ANA public geospatial and hydrological data.

**Recommended stack**: Azure (strong TOTVS partnership) or AWS, Databricks or Azure Synapse for data platform, Power BI for visualization, Azure IoT Hub for sensor integration, ArcGIS/QGIS for spatial analysis.

### Sales hooks that close

1. **"You're leaving R$500K–R$2M on the table with CFEM miscalculations."** Manual spreadsheet calculations have 2–5% error rates. ANM's new PGRM platform makes digital compliance mandatory.
2. **"One missed environmental condicionante can shut you down tomorrow."** Most mid-market miners track license conditions in Excel. A digital tracker with automated alerts is existential risk insurance.
3. **"Post-Brumadinho, dam safety compliance carries criminal liability."** Lei 14.066/2020 applies to ALL mining tailings dams. Non-compliance means personal criminal liability for executives.
4. **"Your fleet management system has data worth millions that nobody reads."** Most miners use only 30–40% of FMS capabilities. Properly analyzing this data yields 5–15% productivity improvement.
5. **"Your geological data and production data don't talk to each other."** Grade dilution from poor blending costs 2–5% of revenue that proper data integration could recover.

---

## VERTICAL 2: Investment advisory offices (Escritório de Investimento)

### A R$7.9 trillion market served by spreadsheets

Brazil's investment advisory market has grown to **~1,384 registered firms** with **26,681 certified advisors** managing access to **R$7.9 trillion** in individual investment volume. The top 10 escritórios by assets under custody range from FAMI Capital (R$75B) to Ável Investimentos (R$15B). Mid-market offices — R$1–15B AuC, 10–80 advisors, 1,000–10,000+ clients — represent the sweet spot for AI consulting.

The revenue model is shifting. Commission-based income (rebates from XP, BTG, Safra at ~0.5–0.7% ROA) still dominates, but **CVM Resolution 179** (fully effective November 2024) mandates transparency on all commissions, creating pressure to demonstrate value. Fee-based models are emerging — Blue3 has 20% of its base on fee-based, targeting 50%. The shift means advisors who can't justify their cost with superior service will lose clients to robo-advisors and fee-based competitors.

Technology adoption is uneven. XP provides CRM tools through its Hub platform, and XP's own data shows that **advisors using CRM properly achieve 2.5x higher client acquisition and 7x NPS improvement**. Yet most escritórios have 5–12 disconnected data sources: platform data, CRM, WhatsApp, Excel spreadsheets, email, consolidation tools (Gorila, SmartBrain), compliance systems, and marketing tools. Advisors spend **6–10 hours per week** on manual report generation alone.

Key tech players serving this market include Gorila (1.5M+ portfolios, R$200B+ in assets, AI-powered natural language portfolio analysis), SmartBrain (450+ clients, R$210B+, received US$10M from Inovabra/Bradesco), Pluggy (Open Finance API covering 18+ institutions, Y Combinator-backed), Louro Tech (R$20B under management, ex-XP founders), and Comdinheiro (R$120B+ consolidated).

### Diagnostic engagement template (R$25K–R$80K, 2–3 weeks)

**Week 1 — Discovery.** Stakeholder interviews with partners/owners, compliance officer, operations lead, and 2–3 senior advisors. Inventory current tech stack: platform tools (XP Hub/CRM, BTG portal), portfolio consolidation (Gorila, SmartBrain, Comdinheiro), external CRM (HubSpot, Pipedrive), communication tools (WhatsApp Business, email). Map data flows. Document key processes: client onboarding, reporting cycles, rebalancing workflows, compliance checks.

**Week 2 — Assessment.** Quantify data fragmentation (typically 5–12 disconnected sources). Conduct manual process audit measuring hours/week on report generation, portfolio monitoring, compliance checks, lead management, and client communications. Perform compliance gap analysis against CVM 178/179, suitability requirements, LGPD data handling, and ANBIMA code. Measure client engagement metrics: contact frequency per segment, NPS/satisfaction, churn rate, AuC growth per advisor. Calculate revenue per advisor efficiency.

**Week 3 — Recommendations.** Deliver prioritized opportunity matrix, quick wins (<30 days) vs. strategic projects (3–6 months), ROI projections for top 3 opportunities, and technology architecture recommendation.

**Key metrics with baseline and target values:**

| Metric | Typical Baseline | AI-Enabled Target |
|--------|-----------------|-------------------|
| Report generation time | 6–10 hrs/week per advisor | <30 min/week |
| Client contacts/month | 1–2 per client | 4–6 (automated + personal) |
| Suitability review cycle | Annual/ad hoc | Continuous monitoring |
| Lead conversion rate | 5–10% | 15–25% |
| Advisor capacity | 100–200 clients | 300–500 clients |
| Churn rate | 8–15%/year | 4–8%/year |

### Implementation playbook

**Project 1: Automated client reporting dashboard** (R$150K–R$300K, 8–12 weeks). Automated pipeline pulling data from XP/BTG APIs and consolidation tools (Gorila API, SmartBrain API), generating AI-personalized reports with performance attribution, benchmark comparisons, and market commentary. A 20-advisor escritório saves 320 hours/month — equivalent to **3–4 FTEs worth R$30K–80K/month** redirected to client acquisition.

**Project 2: CRM intelligence and client segmentation** (R$100K–R$200K, 6–10 weeks). Unified client data layer with AI-driven segmentation: risk profile clusters, life-stage segments, product affinity scoring, communication preference optimization. Key feature: automated "next best action" prompts (e.g., "Client X has 60% in fixed income, profile is moderate, Selic is dropping → suggest rebalancing conversation"). Per XP's data, proper CRM usage drives **2.5x captation increase**.

**Project 3: Compliance and suitability automation** (R$200K–R$350K, 10–14 weeks). Automated compliance monitoring: continuous suitability drift detection, automated CVM 179 transparency disclosures, LGPD consent management, regulatory reporting pipeline. Integrates CVM 178/179, CVM 30 (suitability), ANBIMA Código de Distribuição, and LGPD requirements. ROI: reduces compliance risk (fines up to R$20M for CVM violations), saves 10–15 hours/week of compliance officer time.

**Project 4: Churn prediction and client retention engine** (R$120K–R$250K, 8–12 weeks). ML model trained on behavioral signals: declining login frequency, withdrawal patterns, reduced engagement, external signals via Pluggy Open Finance data. Reducing churn from 12% to 8% on a R$5B AuC escritório at 0.6% ROA = **R$12M in additional retained revenue**.

**Project 5: Lead scoring and prospecting intelligence** (R$80K–R$150K, 6–8 weeks). AI-powered lead scoring integrating demographic data, social signals, estimated investable assets, and behavioral signals from marketing touchpoints. Doubles lead conversion rate from 5% to 10–15%, reduces time-to-close by 40%.

### Reusable solution patterns

- **Multi-source portfolio consolidation pipeline**: API connectors (Gorila Connect, SmartBrain, Pluggy Open Finance) → cloud data lake → normalization layer → analytics engine
- **Natural language portfolio analysis**: LLM layer + structured portfolio data + market context → natural language insights (e.g., advisor asks "which clients are over-exposed to credit risk?")
- **Regulatory compliance event stream**: Portfolio change events → compliance rules engine → alert/action triggers for suitability drift, anti-churning, disclosure automation
- **Client communication orchestration**: Segmentation engine → AI content generation → channel optimization (email, WhatsApp, calls) → engagement tracking → feedback loop
- **Open Finance data enrichment**: Pluggy API → consent management → data aggregation → client 360° view → cross-sell intelligence
- **Intelligent document processing**: OCR/NLP for client onboarding (KYC docs), tax reporting (IR sobre investimentos), contract management

### Quantified client outcome examples

**Report automation**: 8 hours/week per advisor → 15 minutes/week. A 20-advisor escritório redirects 320 hours/month to revenue-generating activity worth **R$40K–80K/month**.

**CRM-driven captation**: From 3 to 7–8 new clients/month per advisor. At R$2M average AuC, 0.6% ROA = additional R$12K/year per new client × 100 additional clients/year = **R$1.2M new annual revenue**.

**Churn reduction**: 12% → 7% annual churn on R$5B AuC = R$250M retained × 0.6% ROA = **R$1.5M/year retained revenue**.

**Lead scoring**: 5% → 15% conversion rate. 10 additional clients/month × R$2M avg AuC × 0.6% ROA = **R$1.44M additional annual revenue**.

### Regulatory and compliance map

| Regulation | Key Requirements |
|-----------|-----------------|
| **CVM 178 (2023)** | New name (assessor de investimento), end of exclusivity, flexible corporate structures, mandatory diretor responsável, termo de ciência |
| **CVM 179 (full effect Nov 2024)** | Mandatory disclosure of all rebates/spreads/distribution fees at point of sale; quarterly extracts to clients |
| **CVM 30/2021** | Suitability verification mandatory before any recommendation; three-element assessment (objectives, financial situation, knowledge) |
| **CVM 50/2021** | Client registration and KYC; max 5-year profile update cycle; investor classification (professional >R$10M, qualified >R$1M) |
| **ANBIMA Código de Distribuição** | Standardized suitability scoring, product complexity classification, advertising rules, privacy controls |
| **LGPD** | Purpose limitation for suitability data, DPO required, incident response plan, client right to access/correct/delete |

### Technical patterns and integration points

**Platform APIs**: XP Investimentos (proprietary CRM Hub, limited external API access), BTG Pactual (multi-account management), Gorila (GorilaVIEW B2B API, 1.5M+ portfolios), SmartBrain (SaaS + API, R$210B+), Pluggy (Open Finance API, 18+ institutions, regulated by Bacen), B3 (market data API), Comdinheiro (portfolio consolidation API, R$120B+).

**Specialized tools**: Louro Tech (front-office platform, multi-platform XP+BTG), AAWZ (back-office commission management), Finvity (financial planning), Exclusive CRM (purpose-built for assessorias), Quantum Finance (fund analysis, rebate data).

**Key integration challenge**: XP/BTG API access is limited; platform data often requires manual export or screenscraping. Data standardization across platforms is difficult. Open Finance Phase 4 (investments) is still maturing. Every data pipeline must have LGPD consent management and audit trails.

### Sales hooks that close

1. **"Your advisors spend 30%+ of their time on non-revenue activities."** 20 advisors × 8 hrs/week × R$150/hr = R$24K/week wasted on reports and data entry.
2. **"CVM 179 transparency is a threat or an opportunity."** Clients now see what they're paying. Escritórios that demonstrate superior value through AI-powered insights retain clients; those that can't lose to robo-advisors.
3. **"XP's own data shows CRM users capture 2.5x more clients."** Ultra Advisors program participants increased captation by 53%. Ask: "What percentage of your advisors consistently use CRM?"
4. **"You're losing R$X million/year to preventable churn."** Calculate: AuC × churn rate × ROA = annual revenue at risk. Reducing churn by 5 percentage points saves millions.
5. **"The fee-based transition requires demonstrating tangible value."** When clients pay a visible fee, they expect a visible service upgrade. AI-powered insights become the differentiator.

---

## VERTICAL 3: Insurance and surety bonds (Seguros e Seguro Garantia)

### Seguro garantia is Brazil's fastest-growing insurance segment

Brazil's insurance market reached **R$751.3B in 2024** (12.2% growth), with the seguro garantia (surety bond) segment emerging as the standout: **R$6.27B in 2025, growing 23.2%** — the fastest-growing segment in Brazilian insurance. The market has doubled since 2020 and is projected to surpass R$10B by 2028. There are now 44 active insurers in the segment, up 22% in five years.

**Pottencial Seguradora** leads with R$1.021B in premiums (16.29% market share, 9th consecutive year as leader), followed by Junto Seguros (JMalucelli/Travelers JV, pioneer since 1992, 80K+ companies guaranteed). Other key players include Ezze Seguros (launched 2019 with guarantee focus, now 250+ employees), Fairfax, Tokio Marine, and Austral. Granto Seguros stands out as a digital-first insurtech with R$10B+ in insured value and API integrations with 15+ insurers.

The growth is structurally driven by **Lei 14.133/2021 (Nova Lei de Licitações)**, which expanded seguro garantia requirements. The law's Article 101 allows guarantees of up to **30% of contract value** with a step-in clause enabling the insurer to take over and complete projects — a game-changer for infrastructure. Some **86.9% of seguro garantia operations** are tied to public sector contracts.

A critical challenge has emerged: the **sinistralidade (loss ratio) rose 16 percentage points to 41.7% in 2025**, making AI-driven claims intelligence and underwriting optimization urgent. Meanwhile, a CNseg/EY study from February 2026 found that while **80% of Brazilian insurers have adopted AI**, only 23% see meaningful impact — the main barrier being legacy system integration (69%).

Brazil's **Lei 15.040/2024** (Marco Legal dos Seguros) entered into force in December 2025, creating a new insurance contract framework requiring 25-day proposal response, 30-day claims response, and enhanced transparency. Open Insurance (OPIN) Phase 3 (service initiation) went live in 2025, making Brazil a global pioneer in open insurance implementation.

### Diagnostic engagement template (R$25K–R$75K, 2–4 weeks)

**Week 1 — Discovery.** Interview CEO/COO, Head of Underwriting, IT Director, Claims Manager, and Compliance Officer. Map current underwriting workflow for seguro garantia from tomador application through credit analysis to policy issuance. Conduct technology audit of core systems (policy admin, CRM, claims, financial). Inventory all data sources used (credit bureaus, SUSEP data, internal databases, court records).

**Weeks 2–3 — Assessment.** Measure underwriting efficiency: time-to-quote, time-to-issue, approval rates, manual vs. automated steps. Benchmark claims processing: average resolution time, documentation requirements, fraud detection capabilities. Evaluate compliance readiness: SUSEP reporting (Circular 662/2022 for seguro garantia, Circular 710/2024 for operations registration), OPIN readiness (Phase 3 APIs), LGPD compliance, Lei 15.040/2024 adaptation status. Assess data integration maturity: silos, API capabilities, real-time data access.

**Week 3–4 — Recommendations.** Gap analysis against market best practices, priority matrix (quick wins vs. strategic initiatives), ROI projections for top 3 initiatives, 6/12/18-month implementation roadmap.

### Implementation playbook

**Project 1: Automated underwriting engine for seguro garantia** (R$400K–R$800K, 4–6 months). AI-powered risk scoring integrating Serasa/Boa Vista credit data, SUSEP policy history, court records (processos judiciais), B3 financial data, and government procurement data (PNCP/ComprasNet). Components: credit scoring ML model, document OCR pipeline, API integrations with data providers, risk dashboard. **Expected ROI: 70–80% reduction in underwriting time, 15–25% increase in throughput.**

**Project 2: SUSEP compliance and reporting dashboard** (R$200K–R$400K, 3–4 months). Automated data extraction from policy admin systems, validation against SUSEP schemas (SRO — Sistema de Registro de Operações), real-time compliance monitoring. Expected ROI: **60% reduction in compliance labor, near-zero reporting errors**.

**Project 3: Open Insurance (OPIN) integration platform** (R$300K–R$600K, 4–6 months). API gateway for OPIN compliance, data sharing orchestration, consent management (LGPD-compliant), competitive intelligence from shared data. FAPI-certified APIs, mTLS, OAuth 2.0, DCR compliance. Creates a new customer acquisition channel.

**Project 4: Claims intelligence and fraud detection** (R$350K–R$700K, 5–7 months). ML-based claims prediction, document verification (OCR + AI), fraud pattern detection, automated triage. With sinistralidade at 41.7%, a **5–10% reduction in loss ratio on R$500M premium base = R$25–40M in reduced claims payout**.

**Project 5: Broker-insurer data exchange platform** (R$250K–R$500K, 3–5 months). API-based platform for real-time quote requests, policy issuance, and status tracking. Embedded insurance capabilities for procurement platforms. **50% reduction in policy issuance time**, new distribution channels.

### Reusable solution patterns

- **Credit risk scoring for tomadores**: CNPJ + financial statements + credit bureau data + court records + SUSEP claims history → ML ensemble model → risk score (0–1000) + premium range + approval recommendation
- **Document intelligence pipeline**: Scanned/PDF documents (editais, apólices, sinistros) → OCR → NLP extraction → structured data → validation → exception queue
- **Regulatory compliance engine**: Policy/operations data → rule-based validation against SUSEP/CNSP requirements + anomaly detection → compliance reports + alerts + audit trails
- **Predictive claims model**: Policy characteristics + tomador profile + contract type + macro indicators → survival analysis + classification models → expected loss + claims probability + early warning
- **Customer 360/broker intelligence**: CRM + policy history + claims + OPIN shared data → segmentation + lifetime value prediction + cross-sell propensity scoring

### Quantified client outcome examples

**Mid-size seguro garantia insurer (R$300M premiums)**: Policy issuance reduced from **5 days to 30 minutes** for standard risks. Underwriting throughput increased 40% without additional headcount. SUSEP reporting effort reduced by 60%. Estimated annual value: R$2–4M in operational savings plus R$5–10M in incremental premiums from faster issuance.

**Large corretora specializing in seguro garantia**: Real-time cotação via API integration with 5+ insurers. Cross-sell identification increased revenue per client by 15–20%. Claims flagging caught 8% of potentially fraudulent claims early. Estimated annual value: **R$1–3M incremental commission plus R$500K in operational savings**.

**Seguradora implementing AI claims management**: Claims resolution time reduced from 45 to 15 days (67% improvement). Loss ratio decreased by 5–8 percentage points. On R$500M premium base: **R$25–40M in reduced claims payout**.

### Regulatory and compliance map

| Regulation | Scope | Key Requirements |
|-----------|-------|-----------------|
| **Circular SUSEP 662/2022** | Seguro garantia regulation | Defines modalities, underwriting requirements (Art. 28: must evaluate tomador + principal contract), claims procedures |
| **Circular SUSEP 710/2024** | Operations registration | Detailed field-level data for SRO registration with credentialed entities |
| **Circular SUSEP 638/2021** | Cybersecurity | Data processing/storage rules, cloud computing governance |
| **Resolução CNSP 415/2021** | Open Insurance | Defines participants (obligatory: S1/S2 segments), data sharing requirements, consent rules |
| **Lei 14.133/2021 Art. 96/101** | Public procurement bonds | Up to 5% guarantee (10% justified), 30% with step-in clause for large works |
| **Lei 15.040/2024** | Insurance contract law | 25-day proposal response, 30-day claims response, transparency requirements (in force Dec 2025) |
| **LGPD** | Data protection | Up to 2% revenue / R$50M per infraction; consent required; OPIN consent aligned |

### Technical patterns and integration points

**Data sources and APIs**: SUSEP Open Data (REST API/CSV at dados.susep.gov.br), PNCP/ComprasNet for procurement data (REST API), Serasa Experian and Boa Vista/Equifax (paid APIs), court record databases (PJe, state TJ systems), Receita Federal CNPJ data (API), CEIS/CNEP sanctioned company data (REST API), B3 Trillia platform (new partnership with CNseg), OPIN APIs (FAPI-certified, OAuth 2.0).

**Key ecosystem players**: Finansystech/Celcoin (Open-as-a-service for OPIN compliance), Agger (broker management platform, 95% of Brazilian municipalities), Granto Seguros (embedded seguro garantia via API), Brick (AI agents for underwriting/fraud, 650+ clients), Autoinsp (AI computer vision for inspections), Segarante (digital seguro garantia platform), Guidewire and Sinqia/Evertec (core insurance systems).

### Sales hooks that close

1. **"Your underwriting takes days; the market demands minutes."** Granto processes cotações in 24 hours. Embedded real-time issuance is becoming table stakes. Companies losing licitações because they can't get a garantia fast enough go to competitors.
2. **"R$6.27B market growing 23% — but your systems can't scale."** Legacy systems built for lower volumes can't handle doubling demand. Every rejected application due to slow processing is lost revenue.
3. **"Sinistralidade rose 16 points to 41.7% — can you afford not to have AI claims intelligence?"** A 5% loss ratio reduction on R$500M is R$25M. The system pays for itself in Q1.
4. **"80% of insurers use AI, but only 23% see real impact."** The barrier is legacy integration, not AI itself. Specialized integration of AI into underwriting, claims, and compliance workflows is where the ROI lives.
5. **"Open Insurance Phase 3 is live — compete or be disrupted."** OPIN service initiation means customers can contract through any platform. First-movers gain the acquisition channel.

---

## VERTICAL 4: Auction market (Mercado de Leilão)

### An exploding market built on fragmented infrastructure

Brazil's auction market is experiencing extraordinary growth: **86% increase in auction volume in 2024**, with 275,000 total transactions moving **R$200 billion**. Caixa Econômica Federal alone auctioned **47,000 properties in 2024** (up from 9,000 in 2022 — a 5x increase), with stock reaching 50,400 units. H1 2025 saw 116,600 properties auctioned, up 25.1% year-over-year. Google searches for "leilão de imóveis" grew over 3,000% in the past 12 months.

Yet the market is remarkably inefficient: **only ~15% of properties brought to auction actually sell**, per ABRAIM data. The buyer profile is 92.6% individuals, 78.5% male, average age 43, with an average arrematação (winning bid) value of R$361,300. Typical discounts run 30–60% below market value, but investors must reserve **40%+ above the lance value** for hidden costs (ITBI 2–3%, leiloeiro commission 5%, cartório fees 1–2%, reforma, legal fees 3–5%, hidden debts like IPTU and condomínio). Caixa spent **R$443M in 2023 on IPTU and condomínio alone** for its unsold property stock.

The core problem is data fragmentation: over **1,000 leiloeiro websites** in Brazil, each with different formats, no standardized data, and no centralized database. Manual edital analysis costs ~R$2,000 per property for lawyer review. Checking a matrícula for encumbrances requires manual cartório visits. Property valuation demands cross-referencing FipeZap, OLX, ZAP, and QuintoAndar data by hand.

AI-powered platforms are already emerging to address this: Leilão Ninja (AI scoring with IPL index, R$200/month), BuscAI Leilões (AI viability/profit calculation), Arremata.ai, Cardeal (AI legal analysis), and GarimpIA. Aggregators like Leilão Imóvel (800+ leiloeiros, 90,478 judicial properties) and Núcleo Leilões provide data consolidation. White-label SaaS provider Sua Plataforma de Leilão serves 100+ leiloeiros.

### Diagnostic engagement template (R$35K–R$75K, 2–3 weeks)

**Week 1 — Discovery.** For auction platform/leiloeiro clients: assess current data sources, platform architecture, scraping capabilities, buyer experience flow. For investor groups/funds: assess deal screening process, legal analysis workflow, valuation methodology, post-arrematação management. Map all data sources: how many auction platforms monitored, what comparison data used, how legal risk is assessed.

**Week 2 — Assessment.** Score AI readiness across 6 dimensions: data aggregation (how many sources integrated, data freshness), valuation accuracy (current method vs. AVM potential), legal risk assessment (manual vs. automated edital/matrícula analysis), deal flow efficiency (properties screened per week, conversion rate), technology stack (platform age, API readiness, mobile experience), post-auction workflow (desocupação management, documentation tracking). Benchmark against emerging AI tools (Leilão Ninja, BuscAI, Arremata.ai).

**Week 3 — Recommendations.** Deliver current-state assessment with data flows and technology gaps, AI readiness score, 3–5 quick wins implementable within 30 days, strategic roadmap with ROI estimates, competitive benchmarking.

### Implementation playbook

**Project 1: Auction aggregation engine** (R$250K–R$400K, 3–4 months). Scrape and normalize data from 500+ leiloeiro sites, Caixa, Banco do Brasil, TJ databases into a unified database with daily refresh. Architecture: Scrapy/Playwright scraping cluster → ETL pipeline → normalized data lake → search/filter API → frontend. **Foundation for all other projects. ROI: 10x more properties analyzed.**

**Project 2: Automated valuation model (AVM)** (R$150K–R$250K, 2–3 months). ML model integrating FipeZap, OLX, ZAP, VivaReal, QuintoAndar comparables with auction properties. Feature engineering on m², bedrooms, location, floor, condition. Output: estimated market value, discount percentage, confidence score. **Reduces valuation time from 4 hours to 30 seconds per property.**

**Project 3: Legal risk scorer** (R$200K–R$350K, 3–5 months). NLP pipeline for edital parsing, matrícula OCR (Azure AI Document Intelligence/Tesseract), certidão cross-referencing. Output: risk score (0–100), flagged issues (ônus, penhoras, hipotecas, pending lawsuits), recommended actions. **Reduces legal analysis cost from R$2,000 to ~R$50 per property.**

**Project 4: Investment scoring dashboard** (R$120K–R$200K, 2–3 months). Combines AVM + legal risk + location analytics + occupancy data into composite score. Investor-facing UI with map visualization, alerts, and portfolio tracking. Enables institutional-grade deal screening at individual investor cost.

**Project 5: Edital parser and alert system** (R$80K–R$150K, 1–2 months). NLP extraction of key terms, deadlines, payment conditions from PDF editais. Push alerts via WhatsApp Business API and email based on investor criteria. **Fastest time-to-value; addresses the #1 investor pain point.** Users receive matching opportunities within 15 minutes of listing.

### Reusable solution patterns

- **Data aggregation pattern**: Web scraping cluster (Scrapy/Playwright) → ETL pipeline → normalized PostgreSQL + Elasticsearch → search/filter API → frontend
- **Document intelligence pattern**: PDF ingestion → OCR (Azure/Google Vision) → NLP extraction (GPT-4/Claude) → structured data → risk scoring rules engine
- **Automated valuation pattern**: Comparable sales data → feature engineering → gradient boosting/neural net model → confidence interval output
- **Alert/notification pattern**: Event-driven architecture (Kafka/RabbitMQ) → user preference matching → WhatsApp Business API/email → engagement tracking
- **Investment scoring pattern**: Multi-factor model (price discount × legal risk × occupancy × location quality × liquidity × reform cost) → weighted composite score
- **Workflow automation pattern**: Post-arrematação task templates → document checklist → deadline tracking → CRM integration → status dashboard

### Quantified client outcome examples

**Auction aggregator for investor platform**: Unified 800+ leiloeiro sources into single search. Users analyze **10x more properties per week** with 70% less time searching.

**AVM for investment fund**: Reduced property valuation time from **4 hours to 30 seconds** per property. Increased deal flow screening by 50x. Improved bid accuracy by 25%.

**Legal risk scorer for law firm**: Automated edital analysis reduced legal review cost from **R$2,000 to R$50 per property**. Reduced risk incidents by 40%. Scaled from 20 to 200 analyses per month.

**Alert system for individual investors**: Users receive matching opportunities within **15 minutes of listing**. Early access increased successful arrematação rate by 35%.

**Post-auction workflow for advisory firm**: Reduced time-to-registration from **9 months to 4 months**. Automated 60% of post-arrematação tasks.

### Regulatory and compliance map

| Regulation | Key Requirements | AI Implications |
|-----------|-----------------|----------------|
| **CPC/2015 Arts. 879–903** | Judicial auction rules: edital requirements, preço vil prohibition, 25% + 30 installment payment | AI recommendations must comply with minimum price rules |
| **Lei 9.514/1997** | Alienação fiduciária; two-auction system; debtor notification; 30-day auction deadline | Extrajudicial pipeline must track notification compliance |
| **Lei 14.133/2021** | Nova Lei de Licitações for government asset disposal | Government auction platform integration compliance |
| **CNJ Resolução 236/2016** | Electronic auction regulation: leiloeiro credenciamento (min. 3 years), 5% commission, 5-day minimum pre-lance, 3-minute extension rule | Platform design must comply with timing rules |
| **Lei 14.711/2023** | Updates to alienação fiduciária procedures | Integration updates for extrajudicial auction tracking |
| **LGPD** | Data protection for scraped/aggregated data, investor data handling, debtor data protection | Scraping must respect personal data; debtor names may be PII |

Tax implications for buyers: ITBI (typically 2–3% of arrematação value, varies by municipality), IR sobre ganho de capital on resale (15–22.5%), leiloeiro commission (typically 5% per CNJ Res. 236), and potential liability for outstanding IPTU and condomínio debts depending on auction type and edital terms.

### Technical patterns and integration points

**Primary data sources**: Caixa Econômica Federal property API (structured data via Apify: evaluationValue, minimumSaleValue, discount, area, matriculaUrl, paymentMethods), Santander property API (Apify), FipeZap/DataZap (price indices for 50+ cities, Excel download), QuintoAndar/OLX/ZAP scrapers (Apify marketplace), TJ databases per state (27 different systems), Receita Federal SLE (e-CAC portal), Geoimovel (proptech with AI location/price mapping).

**Key technical challenges**: No unified property identifier across systems (matrícula numbers are cartório-specific). Over 1,000 leiloeiro websites with heterogeneous formats, JavaScript rendering, CAPTCHAs, and session-based authentication. TJ portals vary by state with anti-scraping measures. Many editais are PDF documents requiring OCR. Property addresses need geocoding for map visualization.

**Recommended stack**: Playwright/Puppeteer for JS-heavy sites, rotating proxies, PostgreSQL + Elasticsearch for structured + full-text search, Redis for caching, Kafka/RabbitMQ for real-time alert processing, React/Next.js with Mapbox for geolocation visualization, Azure AI Document Intelligence or Tesseract for OCR, Portuguese-trained LLMs for legal text interpretation.

### Sales hooks that close

1. **"You're missing 90% of opportunities."** With 1,000+ leiloeiro sites and no centralized database, even professional investors screen only a fraction of available deals.
2. **"R$2,000 per property analysis is killing your margins."** AI drops this to R$50, enabling screening of 200+ properties where you currently analyze 20.
3. **"The 15% sell-through rate reveals a broken market."** Better matching, valuation accuracy, and risk assessment dramatically improve outcomes for both sellers and buyers.
4. **"Hidden costs eat your 40% discount."** AI risk scoring identifies hidden debts (IPTU, condomínio, penhoras) before you bid, protecting margins.
5. **"The market grew 86% but your tools didn't."** Spreadsheets and manual searches can't scale with volume that doubled in one year.
6. **"From 4 hours to 30 seconds."** Replace manual comparable market analysis with instant AI-powered valuation using data from 20+ real estate portals.

---

## Cross-vertical patterns and the productization opportunity

### Three engagement patterns repeat across all four verticals

**Pattern 1: Compliance automation as the entry point.** In every vertical, regulatory compliance is both the most acute pain and the easiest "yes." CFEM/ANM reporting in mining, CVM 178/179 suitability in investment advisory, SUSEP/OPIN in insurance, and CPC/Lei 9.514 compliance in auctions — all involve manual processes with severe penalties for failure. A compliance automation diagnostic surfaces quantifiable waste and risk, making the paid assessment an easy decision.

**Pattern 2: Data integration as the foundation project.** Every vertical suffers from 5–12 disconnected systems. The first implementation project is always a data integration layer — connecting ERP to mine planning, platform data to CRM, policy admin to credit bureaus, or 1,000 auction sites to a unified database. This integration layer becomes the foundation for all subsequent AI capabilities.

**Pattern 3: AI-powered decision support as the value multiplier.** Once data is integrated, the same ML patterns recur: predictive models (churn, equipment failure, claims, investment returns), document intelligence (NLP for editais, compliance documents, portfolio reports), scoring engines (risk scoring for tomadores, leads, auction properties, environmental compliance), and automated alerting. These patterns can be built as reusable components across verticals.

### Pricing the engagement arc

| Stage | Mining | Investment | Insurance | Auctions |
|-------|--------|------------|-----------|----------|
| **Diagnostic** | R$25K–75K | R$25K–80K | R$25K–75K | R$35K–75K |
| **First implementation** | R$150K–350K | R$100K–200K | R$200K–400K | R$80K–150K |
| **Full 12-month portfolio** | R$1.3M–3M | R$650K–1.25M | R$1.5M–3M | R$800K–1.35M |
| **Ongoing retainer** | R$30K–80K/mo | R$15K–40K/mo | R$25K–60K/mo | R$15K–40K/mo |

The total addressable market across these four verticals runs into hundreds of potential mid-market clients: Brazil has thousands of mid-market mining operations, 1,384 registered investment advisory firms, 44+ seguro garantia insurers plus hundreds of corretoras, and a rapidly growing ecosystem of auction platforms, leiloeiros, and professional investor groups. A productized AI consulting firm that builds reusable solution components across these verticals can achieve significant operating leverage — the same document intelligence pipeline serves editais in auctions, apólices in insurance, and environmental licenses in mining. The same compliance automation patterns apply whether the regulator is ANM, CVM, or SUSEP. The same churn prediction methodology works for investment clients and insurance policyholders. This cross-vertical reusability is the key to building a scalable, profitable AI consulting business rather than a bespoke services firm.