---
title: Client/Entity 360 Pattern
type: pattern
language: en
last_compiled: 2026-04-02
sources:
  - kb/raw/industry-templates.md
freshness: current
tags:
  - client-360
  - entity-view
  - aggregation
  - cross-vertical
verticals:
  - mining
  - investment-advisory
  - insurance-surety
---

# Client/Entity 360 (Unified Views)

The 360-degree view pattern aggregates all available data about a customer, asset, or entity into a single comprehensive profile. This pattern applies to three of the four verticals, with the "entity" varying by context: clients in investment advisory, customers and brokers in insurance, and physical assets in mining.

## Vertical Implementations

| Vertical | Entity Type | Name | Core Data Domains | Primary Consumer |
|----------|-----------|------|-------------------|-----------------|
| **Investment Advisory** | Client (pessoa fisica/juridica) | Client 360 | Portfolio holdings + behavioral data + risk profile + engagement history + Open Finance data + suitability status | Individual advisors, compliance officers |
| **Insurance/Surety Bonds** | Customer (tomador/segurado) + Broker (corretor) | Customer 360 + Broker Intelligence | Policy history + claims history + credit profile + OPIN shared data + SUSEP data + broker performance metrics | Underwriters, relationship managers, distribution heads |
| **Mining** | Physical asset (equipment, mine site) | Asset 360 | Equipment telemetry + production data + compliance status + maintenance history + cost data | Operations managers, maintenance planners, mine managers |

## Common Architecture

```
[Data Sources]  →  [Aggregation Layer]  →  [Entity Store]  →  [Scoring/Segmentation]  →  [Consumption Layer]
```

### Stage 1: Data Sources

**Investment Advisory -- Client 360:**
- Platform data (XP Hub/BTG portal): portfolio holdings, transactions, account balances
- Consolidation tools (Gorila API, SmartBrain API, Comdinheiro): multi-platform portfolio view
- Open Finance (Pluggy API): cross-institutional holdings (18+ institutions), account data with client consent
- CRM (HubSpot, Pipedrive, Exclusive CRM): interaction history, meeting notes, communication logs
- WhatsApp Business: conversation history, response patterns
- Marketing tools: email engagement, content consumption
- Compliance systems: suitability assessments (CVM 30), risk profile history, KYC data (CVM 50)
- External enrichment: estimated net worth, social signals, life-stage indicators

**Insurance/Surety Bonds -- Customer 360 + Broker Intelligence:**
- Policy admin system (Guidewire, Sinqia): active policies, coverage, premiums, endorsements
- Claims system: claims history, resolution outcomes, payout amounts
- Credit bureaus (Serasa, Boa Vista): credit scores, financial health indicators
- Court records (PJe, state TJ systems): litigation history for tomadores
- SUSEP Open Data: industry-wide policy and claims data
- OPIN APIs (Phase 3): shared insurance data across participants with client consent
- B3 Trillia platform: financial data via CNseg partnership
- CRM: relationship history, touchpoints
- Broker-specific: production volume, loss ratios, portfolio composition, commission history

**Mining -- Asset 360:**
- Fleet Management System (DISPATCH, MineStar, Hexagon): real-time location, utilization, cycle times
- OEM telemetry (Cat Product Link, Komatsu KOMTRAX): engine hours, fuel consumption, diagnostic codes
- Maintenance management system: work orders, parts inventory, maintenance schedules
- Mine planning software (Surpac, Deswik): planned vs. actual production
- Environmental sensors: vibration, temperature, emissions near equipment
- ERP (TOTVS Protheus): cost accounting, spare parts procurement, depreciation
- Safety system: incident reports near equipment, NR-22 compliance records

### Stage 2: Aggregation Layer

- **Entity resolution**: Match records across systems to the same entity (client, tomador, equipment unit). Handle variations in identifiers (CPF/CNPJ, equipment serial numbers, policy numbers).
- **Temporal aggregation**: Combine point-in-time snapshots into a historical timeline. Track how the entity profile evolves over time.
- **Conflict resolution**: When sources disagree (e.g., different addresses, conflicting credit scores), apply precedence rules (most recent, most authoritative source).
- **Freshness management**: Different data sources update at different frequencies. Track last-updated timestamps per data domain and flag stale data.

### Stage 3: Entity Store

- Unified profile record combining all data domains
- Optimized for read-heavy access patterns (advisors, underwriters, managers querying profiles)
- Support for both current-state views and historical timelines
- Schema flexible enough to accommodate new data sources without migration
- **Technology**: Document store (MongoDB, Elasticsearch) for flexible schema, or star-schema in data warehouse with materialized views

### Stage 4: Scoring and Segmentation

Each vertical produces different scores and segments from the aggregated entity data:

**Investment Advisory:**

| Output | Method | Business Use |
|--------|--------|-------------|
| Client lifetime value (CLV) | Historical AuC growth + engagement + tenure | Prioritize advisor attention; justify fee-based pricing |
| Churn risk score | ML model (see [predictive-models.md](predictive-models.md)) | Proactive retention outreach |
| Product affinity score | Collaborative filtering on portfolio composition + profile | Cross-sell recommendations |
| Engagement score | Weighted sum of login, report views, meeting attendance, communication responses | Identify disengaging clients early |
| Risk profile cluster | K-means/hierarchical clustering on investment behavior, not just stated profile | Detect suitability drift (CVM 30 compliance) |
| Life-stage segment | Demographics + financial indicators + behavioral signals | Tailor communication and product offers |

**Insurance/Surety Bonds:**

| Output | Method | Business Use |
|--------|--------|-------------|
| Credit risk score (0-1000) | ML ensemble on financials + credit bureau + court records + SUSEP history | Underwriting decisions; premium pricing |
| Claims propensity | Survival analysis on policy and tomador characteristics | Reserve estimation; pricing optimization |
| Cross-sell propensity | Product affinity model on policy history + profile | Revenue growth per customer |
| Customer lifetime value | Premium history + claims history + retention probability | Relationship investment prioritization |
| Broker performance score | Production volume + loss ratios + retention rates + growth | Distribution strategy; broker tier management |
| Fraud risk indicator | Anomaly detection on claims patterns + network analysis | Claims triage; investigation prioritization |

**Mining:**

| Output | Method | Business Use |
|--------|--------|-------------|
| Equipment health score | ML on telemetry trends + maintenance history + age/hours | Maintenance planning; replacement decisions |
| Failure probability (time horizon) | Survival analysis on operating data | Schedule preventive maintenance; avoid unplanned downtime |
| Utilization efficiency | Actual vs. planned utilization from FMS data | Fleet optimization; identify underperforming units |
| Compliance status | Rule-based check against NR-22, environmental requirements | Prevent regulatory violations |
| Total cost of ownership | ERP cost data + maintenance + fuel + depreciation aggregation | Lease vs. buy decisions; fleet composition planning |

### Stage 5: Consumption Layer

- **Advisor/underwriter dashboard**: Single-page entity profile with all domains, scores, and recommended actions
- **API**: Programmatic access for other systems (alert engine, compliance automation, reporting)
- **Natural language query**: LLM layer enabling questions like "which clients are over-exposed to credit risk?" (investment) or "which trucks have highest failure risk this month?" (mining)
- **Mobile view**: Summarized profile accessible on mobile devices for field use (mining site visits, client meetings)

## Implementation Considerations

### Data Privacy and Consent
- Investment advisory: Open Finance data (Pluggy) requires explicit client consent per Bacen regulation; LGPD purpose limitation applies to suitability data
- Insurance: OPIN consent must be LGPD-aligned; customer data sharing rules per Resolucao CNSP 415/2021
- Mining: Less PII concern for equipment data, but employee safety data (NR-22 incidents) has privacy implications
- All verticals: implement consent management, data access audit trails, right-to-deletion support

### Incremental Build
- Start with the 2-3 most valuable data domains per vertical, not all at once
- Investment: platform portfolio data + CRM first (immediate advisor value)
- Insurance: policy admin + credit bureau first (immediate underwriting value)
- Mining: FMS telemetry + maintenance records first (immediate operations value)
- Add remaining sources over subsequent sprints as integration layer matures

### Data Freshness vs. Cost
- Real-time updates for high-frequency data (equipment telemetry, portfolio positions)
- Near-real-time (hourly/daily) for medium-frequency data (CRM interactions, claims updates)
- Periodic batch for slow-changing data (credit bureau refreshes, financial statements)
- Balance API call costs against freshness requirements (credit bureau calls are expensive)

## Estimated Investment

| Vertical | Scope | Investment Range | Timeline |
|----------|-------|-----------------|----------|
| **Investment Advisory** | Client 360 with portfolio + CRM + engagement + scoring | R$100K-R$200K | 6-10 weeks |
| **Insurance** | Customer 360 + broker intelligence with credit scoring | R$250K-R$500K | 3-5 months |
| **Mining** | Asset 360 with telemetry + maintenance + compliance | R$300K-R$700K | 12-16 weeks |

## Cross-References

- Depends on: [data-integration.md](data-integration.md) (unified data layer provides source data)
- Incorporates: [predictive-models.md](predictive-models.md) (scores become part of entity profile)
- Enriched by: [document-intelligence.md](document-intelligence.md) (extracted document data feeds profile)
- Consumed by: [alert-notification.md](alert-notification.md) (entity context enables personalized alerts)
- Investment: natural language query layer relates to Gorila's AI-powered natural language portfolio analysis
