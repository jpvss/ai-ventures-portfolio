---
title: Cross-Vertical Pattern Library Index
type: index
language: en
last_compiled: 2026-04-02
sources:
  - kb/raw/industry-templates.md
freshness: current
tags:
  - patterns
  - cross-vertical
  - index
---

# Cross-Vertical Pattern Library

Reusable solution patterns that recur across multiple JP Ventures verticals (Mining, Investment Advisory, Insurance/Surety Bonds, Auctions). Each pattern file documents how the same architectural approach manifests differently per industry, enabling component reuse and accelerated delivery.

## Pattern Catalog

| Pattern | File | Mining | Investment | Insurance | Auctions | Description |
|---------|------|:------:|:----------:|:---------:|:--------:|-------------|
| Compliance Automation | [compliance-automation.md](compliance-automation.md) | X | X | X | X | Regulatory compliance engines with rules-based validation and automated reporting |
| Data Integration | [data-integration.md](data-integration.md) | X | X | X | X | Multi-source ETL into unified data layers from 5-12 disconnected systems |
| Document Intelligence | [document-intelligence.md](document-intelligence.md) | X | | X | X | OCR + NLP pipelines for extracting structured data from unstructured documents |
| Predictive Models | [predictive-models.md](predictive-models.md) | X | X | X | X | ML scoring and prediction models for decision support |
| Alert & Notification | [alert-notification.md](alert-notification.md) | X | X | X | X | Event-driven alerting with multi-channel delivery |
| Client/Entity 360 | [client-360.md](client-360.md) | X | X | X | | Unified views aggregating all data about a customer or asset |

## How Patterns Relate to Engagements

These patterns map to the three-stage engagement arc described in `kb/raw/industry-templates.md`:

1. **Compliance automation** is the typical entry point (diagnostic surfaces quantifiable waste and regulatory risk).
2. **Data integration** is always the foundation project (connects 5-12 siloed systems into a unified layer).
3. **Predictive models**, **document intelligence**, **alerts**, and **client 360** are value multipliers built on top of the integrated data layer.

## Cross-References

- Vertical-specific implementations: `kb/verticals/*/solution-patterns.md`
- Engagement templates: `kb/verticals/*/engagement-templates.md`
- Source material: `kb/raw/industry-templates.md`
