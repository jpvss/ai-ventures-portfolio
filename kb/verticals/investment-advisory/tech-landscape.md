---
title: "Investment Advisory — Technology Landscape"
type: tech-landscape
vertical: investment-advisory
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [investment-advisory, technology, systems, apis, data-sources, open-finance]
---

# Investment Advisory — Technology Landscape

## Common Client Systems

| System Type | Common Products | Integration Method | Notes |
|-------------|----------------|-------------------|-------|
| Investment Platform | XP Investimentos (Hub/CRM) | Proprietary API (limited external access) | Dominant platform; CRM included but underutilized |
| Investment Platform | BTG Pactual | Portal + API (multi-account management) | Growing platform; better API access than XP |
| Portfolio Consolidation | Gorila | GorilaVIEW B2B API | 1.5M+ portfolios, R$200B+ assets; AI-powered natural language analysis |
| Portfolio Consolidation | SmartBrain | SaaS + API | 450+ clients, R$210B+; backed by Inovabra/Bradesco (US$10M) |
| Portfolio Consolidation | Comdinheiro | API | R$120B+ consolidated; established but less modern |
| Open Finance | Pluggy | REST API | 18+ institutions; Y Combinator-backed; regulated by Bacen |
| Front-Office | Louro Tech | Platform integration | R$20B under management; multi-platform (XP+BTG); ex-XP founders |
| CRM (External) | HubSpot, Pipedrive | REST API | General-purpose; not financial-specific |
| CRM (Purpose-Built) | Exclusive CRM | API | Built for assessorias; narrower than general CRM |
| Back-Office | AAWZ | API/export | Commission management specialist |
| Financial Planning | Finvity | API/export | Financial planning tools for advisors |
| Fund Analysis | Quantum Finance | API/export | Fund analysis, rebate data |
| Communication | WhatsApp Business | WhatsApp Business API | Primary client communication channel in Brazil |
| Market Data | B3 | Market data API | Official exchange data |

## Data Sources

### Platform APIs

| Source | Data Available | Access Method | Limitations |
|--------|---------------|--------------|-------------|
| XP Investimentos | Portfolio positions, transactions, CRM data | Proprietary Hub API | **Limited external API access**; often requires manual export or screenscraping; platform-locked data |
| BTG Pactual | Portfolio positions, multi-account management | Portal + API | Better API access than XP but still limited for third-party integration |
| B3 | Market data, pricing, corporate actions | REST API | Public/commercial tiers available |

### Portfolio Consolidation APIs

| Provider | Data Available | Scale | Integration |
|----------|---------------|-------|-------------|
| Gorila | Portfolio consolidation, performance attribution, AI natural language analysis | 1.5M+ portfolios, R$200B+ | GorilaVIEW B2B API; Connect API for data ingestion |
| SmartBrain | Portfolio consolidation, analytics, reporting | 450+ clients, R$210B+ | SaaS + API; strong analytics layer |
| Comdinheiro | Asset consolidation, reporting | R$120B+ | API available; legacy architecture |

### Open Finance (Bacen-regulated)

| Provider | Data Available | Coverage | Status |
|----------|---------------|----------|--------|
| Pluggy | Account balances, transactions, investments across institutions | 18+ institutions | Phase 4 (investments) still maturing; Y Combinator-backed; developer-friendly API |

### Client Internal Data

- CRM records (contact history, deal pipeline, client preferences)
- WhatsApp conversation history (primary communication channel)
- Email communications
- Excel spreadsheets (client notes, manual tracking, ad hoc analysis)
- Compliance records (suitability assessments, KYC documents)
- Marketing tool data (campaign engagement, lead sources)

## Integration Patterns

### Pattern 1: Platform Data Extraction (XP/BTG)

**Source:** XP Hub, BTG Portal
**Method:** API where available; structured data export; screenscraping as last resort
**Challenges:** XP API access is limited and proprietary; data schemas differ between platforms; real-time access often unavailable
**Solution:** Hybrid approach — use API for available endpoints, scheduled exports for the rest, normalization layer to unify schemas across platforms

### Pattern 2: Portfolio Consolidation Integration (Gorila/SmartBrain)

**Source:** Gorila GorilaVIEW API, SmartBrain API
**Method:** REST API
**Challenges:** Different data models between providers; asset classification inconsistencies; historical data depth varies
**Solution:** Canonical data model with provider-specific adapters; reconciliation logic for cross-provider positions

### Pattern 3: Open Finance Enrichment (Pluggy)

**Source:** Pluggy Open Finance API
**Method:** REST API with OAuth consent flow
**Challenges:** Phase 4 (investments) still maturing; consent must be explicitly managed under LGPD; data freshness varies by institution; not all institutions fully compliant
**Solution:** Consent management layer; graceful degradation when data unavailable; incremental enrichment (add institutions as consent is obtained)

### Pattern 4: Communication Channel Integration (WhatsApp)

**Source:** WhatsApp Business API
**Method:** Official WhatsApp Business API
**Challenges:** Message templates must be pre-approved; rate limits; conversation history extraction requires careful LGPD consent
**Solution:** Template-based automated messages for reports/alerts; manual advisor messages tracked via CRM integration

## Key Integration Challenges

1. **XP/BTG API access is limited**: Platform data often requires manual export or screenscraping — this is the single biggest technical challenge in the vertical
2. **Data standardization across platforms**: Asset classification, transaction types, and fee structures differ between XP, BTG, and other platforms
3. **Open Finance Phase 4 (investments) is still maturing**: Coverage is incomplete; not all institutions expose investment data yet
4. **LGPD consent architecture**: Every data pipeline must include consent management and audit trails — adds complexity to every integration
5. **Real-time vs. batch**: Most platform data is available in batch (daily/weekly exports) not real-time, limiting the responsiveness of alerts and dashboards

## Recommended Tech Stack

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| Data Ingestion | Python (requests, aiohttp) + Airflow/Prefect | Handles diverse API formats; orchestrates batch and near-real-time pipelines |
| Consent Management | Custom LGPD consent layer | Required for every data source; audit trail mandatory |
| Storage | Cloud data lake (AWS S3 / GCP Cloud Storage) + PostgreSQL | Scalable for portfolio data volume; relational for client profiles |
| Processing | dbt for transformations; Python for ML | SQL-based transformations accessible to analysts; Python for ML models |
| ML/AI | scikit-learn, LangChain/LlamaIndex for NLP | Churn prediction, lead scoring, natural language portfolio analysis |
| Visualization | Streamlit or Retool for advisor dashboards | Rapid prototyping; advisor-friendly UX; lower cost than custom front-end |
| Report Generation | Python (reportlab, jinja2) + AI (GPT-4/Claude) | Automated personalized reports with AI-generated commentary |
| Communication | WhatsApp Business API + email (SendGrid/SES) | Primary channels for Brazilian advisory clients |
| Deployment | AWS or GCP | Cloud-agnostic preference; avoid Azure dependency unless client requires |

## Platform Limitations Summary

| Platform | What Works | What Doesn't | Workaround |
|----------|-----------|-------------|------------|
| XP Hub | Basic CRM, position data via Hub | Limited external API; no real-time feed; data export restrictions | Scheduled exports + screenscraping where permitted |
| BTG Portal | Multi-account management | External API still limited | Better than XP but similar workarounds needed |
| Gorila | Excellent API (GorilaVIEW, Connect); AI features | Consolidation scope depends on data fed in | Use as consolidation layer; feed from multiple platforms |
| SmartBrain | Good analytics; strong SaaS | API depth varies by plan | Enterprise plan for full API access |
| Pluggy | Developer-friendly; Bacen-regulated | Phase 4 (investments) incomplete; institution coverage gaps | Graceful degradation; incremental rollout |

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
