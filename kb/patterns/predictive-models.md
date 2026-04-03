---
title: Predictive Models Pattern
type: pattern
language: en
last_compiled: 2026-04-02
sources:
  - kb/raw/industry-templates.md
freshness: current
tags:
  - predictive-models
  - machine-learning
  - scoring
  - cross-vertical
verticals:
  - mining
  - investment-advisory
  - insurance-surety
  - auctions
---

# Predictive Models (ML Scoring and Prediction)

Once data integration provides a unified data layer, ML-powered prediction and scoring models become the primary value multiplier. The same pipeline architecture and model families recur across verticals, with domain-specific features and target variables.

## Vertical Implementations

| Vertical | Model Type | Target Variable | Key Features | Business Impact |
|----------|-----------|-----------------|-------------|-----------------|
| **Mining** | Equipment failure prediction | Time-to-failure, failure type | OEM telemetry (Cat Product Link, Komatsu KOMTRAX), FMS data, maintenance history, operating conditions | 30-50% reduction in unplanned downtime; R$225K-R$2.5M/year savings on a 50-unit fleet |
| **Mining** | Ore grade optimization | Head grade, blending ratios | Block model data, drilling assays, stockpile inventory, quality constraints | 2-5% improvement in head grade; significant revenue uplift |
| **Investment Advisory** | Churn prediction | Client departure probability | Login frequency, withdrawal patterns, engagement decline, Pluggy Open Finance signals, AuC trends | Reducing churn 12% to 8% on R$5B AuC at 0.6% ROA = R$12M retained revenue |
| **Investment Advisory** | Lead scoring | Conversion probability | Demographics, social signals, estimated investable assets, marketing touchpoints, behavioral data | Doubles conversion rate from 5% to 10-15%; reduces time-to-close by 40% |
| **Insurance** | Claims prediction | Claims probability, expected loss | Policy characteristics, tomador profile, contract type, macro indicators, SUSEP claims history | 5-10% loss ratio reduction on R$500M base = R$25-40M in reduced payouts |
| **Insurance** | Fraud detection | Fraud probability | Claims patterns, document anomalies, network analysis, historical fraud indicators | Caught 8% of potentially fraudulent claims early in case study |
| **Insurance** | Credit risk scoring | Risk score (0-1000) | CNPJ + financial statements + credit bureau + court records + SUSEP history | 70-80% reduction in underwriting time; 15-25% throughput increase |
| **Auctions** | AVM (Automated Valuation Model) | Estimated market value | m2, bedrooms, location, floor, condition, FipeZap/OLX/ZAP/QuintoAndar comparables | Valuation from 4 hours to 30 seconds; bid accuracy improved 25% |
| **Auctions** | Legal risk scoring | Risk score (0-100) | Edital terms, matricula encumbrances, pending lawsuits, debtor profile, property type | Risk incidents reduced 40%; analysis scaled from 20 to 200/month |

## Common ML Pipeline

```
[1. Feature Store]  →  [2. Feature Engineering]  →  [3. Model Training]  →  [4. Evaluation]  →  [5. Serving]  →  [6. Monitoring]
```

### Stage 1: Feature Store
- Centralized repository of curated features derived from the unified data layer
- Shared across models within a vertical (e.g., client engagement features used by both churn and lead scoring models)
- Point-in-time correctness to prevent data leakage during training
- Feature versioning and lineage tracking

### Stage 2: Feature Engineering Patterns

**Temporal features** (recur in every vertical):
- Rolling aggregates (7-day, 30-day, 90-day windows): transaction counts, engagement frequency, production volumes, claim counts
- Trend indicators: increasing/decreasing patterns over time
- Seasonality encoding: month, quarter, business cycles
- Time-since-event: days since last login, last claim, last maintenance, last bid

**Behavioral features** (Investment, Insurance):
- Engagement scoring: login frequency, report views, communication responses
- Transaction patterns: withdrawal velocity, rebalancing frequency, premium payment regularity
- Channel preference: WhatsApp vs. email vs. phone interaction ratios

**Operational features** (Mining):
- Equipment utilization rates, cycle times, fuel consumption
- Environmental sensor readings: vibration, temperature, pressure trends
- Production metrics: tons processed, grade achieved vs. planned

**Financial features** (Insurance, Investment, Auctions):
- Credit bureau scores and trends (Serasa, Boa Vista)
- Financial statement ratios (liquidity, leverage, profitability)
- Market value indicators (FipeZap indices, comparable sales)

**Text-derived features** (Auctions, Insurance):
- NLP-extracted risk indicators from legal documents
- Sentiment and complexity scores from document text
- Entity counts (encumbrances, parties, conditions)

### Stage 3: Model Types by Use Case

| Use Case | Recommended Models | Why |
|----------|-------------------|-----|
| **Binary classification** (churn, fraud, claims) | XGBoost, LightGBM, Random Forest | Tabular data; interpretable; strong with mixed feature types; fast training |
| **Regression** (property valuation, expected loss) | Gradient Boosting (XGBoost/LightGBM), Neural Networks | Continuous output; handles non-linear relationships |
| **Survival analysis** (time-to-failure, time-to-churn) | Cox Proportional Hazards, Random Survival Forests | Models censored data (equipment still running, client still active) |
| **Anomaly detection** (fraud, equipment anomalies) | Isolation Forest, Autoencoders, One-Class SVM | Unsupervised; works with limited labeled fraud/failure examples |
| **Scoring / ranking** (lead scoring, investment scoring) | Learning-to-Rank, weighted multi-factor models | Produces ordered rankings; combines multiple signals |
| **Multi-factor composite scores** (auction investment score, credit risk) | Weighted ensemble of specialized models | Price discount x legal risk x occupancy x location x liquidity x reform cost |

### Stage 4: Evaluation
- Train/validation/test splits respecting temporal ordering (no future data leakage)
- Business-relevant metrics alongside statistical metrics (e.g., revenue impact of false negatives, not just AUC)
- Fairness assessment where applicable (LGPD considerations)
- Backtesting against historical outcomes

### Stage 5: Serving
- Real-time scoring API for interactive use cases (lead scoring, property valuation, underwriting)
- Batch scoring for periodic updates (monthly churn scores, quarterly risk reassessments)
- Score explanation layer (SHAP values, feature importance) for regulated environments where decisions must be explainable

### Stage 6: Monitoring
- Model drift detection: feature distribution shifts, prediction distribution changes
- Performance decay tracking: compare ongoing predictions against actuals
- Automated retraining triggers when performance drops below threshold
- A/B testing framework for model updates

## Implementation Considerations

### Explainability Requirements
- CVM 30 (suitability) and SUSEP underwriting regulations may require explainable recommendations
- LGPD Article 20 grants data subjects the right to request review of automated decisions
- Use SHAP/LIME for model explanations; maintain human-in-the-loop for high-stakes decisions
- Document model methodology for regulatory audit purposes

### Data Volume Realities
- Mid-market Brazilian companies often have limited historical data (hundreds to low thousands of records)
- Use techniques suited to small datasets: gradient boosting over deep learning, transfer learning, synthetic data augmentation
- Start with simpler models (logistic regression, decision trees) and increase complexity as data grows
- External data enrichment (credit bureaus, market data) compensates for limited internal data

### Cold Start
- New deployments lack historical outcome data for training
- Use rule-based scoring initially (expert-defined heuristics)
- Transition to ML models after 6-12 months of data collection
- Hybrid approach: ML predictions weighted with expert rules during transition

## Estimated Investment

| Vertical | Model Scope | Investment Range | Timeline |
|----------|------------|-----------------|----------|
| **Mining** | Equipment failure prediction + ore grade optimization | R$400K-R$1M | 16-24 weeks |
| **Investment** | Churn prediction + lead scoring | R$200K-R$400K | 8-12 weeks each |
| **Insurance** | Claims prediction + fraud detection + credit risk scoring | R$350K-R$700K | 5-7 months |
| **Auctions** | AVM + legal risk scoring | R$350K-R$600K | 5-8 months |

## Cross-References

- Depends on: [data-integration.md](data-integration.md) (unified data layer provides features)
- Depends on: [document-intelligence.md](document-intelligence.md) (text-derived features)
- Feeds into: [alert-notification.md](alert-notification.md) (model outputs trigger alerts)
- Feeds into: [client-360.md](client-360.md) (scores become part of entity profile)
