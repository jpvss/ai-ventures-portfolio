---
title: Data Integration Pattern
type: pattern
language: en
last_compiled: 2026-04-02
sources:
  - kb/raw/industry-templates.md
freshness: current
tags:
  - data-integration
  - ETL
  - data-platform
  - cross-vertical
verticals:
  - mining
  - investment-advisory
  - insurance-surety
  - auctions
---

# Data Integration (Multi-Source Data Platform)

Every vertical AI Ventures serves has 5-12 disconnected systems that do not communicate. Data integration is always the foundation project -- the first implementation after a diagnostic engagement -- because all subsequent AI capabilities (predictive models, document intelligence, alerting, client 360) depend on a unified data layer.

## Vertical Implementations

| Vertical | Typical System Count | Key Source Systems | Core Integration Challenge |
|----------|---------------------|-------------------|--------------------------|
| **Mining** | 5-8 systems | TOTVS Protheus (ERP), GEOVIA Surpac/Deswik/Vulcan (mine planning), Modular DISPATCH/Cat MineStar/Hexagon (fleet management), LIMS (lab data), environmental sensors, ANM systems | Geological models never flow automatically to production systems; CFEM calculations happen in Excel |
| **Investment Advisory** | 5-12 systems | XP Hub/BTG portal (platform data), Gorila/SmartBrain/Comdinheiro (consolidation), HubSpot/Pipedrive (CRM), WhatsApp, Excel, email, marketing tools | XP/BTG API access is limited; platform data often requires manual export or screenscraping; LGPD consent management required |
| **Insurance/Surety Bonds** | 5-10 systems | Core policy admin (Guidewire/Sinqia), CRM, claims system, Serasa/Boa Vista (credit bureaus), SUSEP Open Data, court records, OPIN APIs, B3 Trillia | Legacy system integration (69% of insurers cite as main AI barrier per CNseg/EY 2026); FAPI-certified API requirements for OPIN |
| **Auctions** | 1,000+ sources | 1,000+ leiloeiro websites, Caixa/Santander property APIs, FipeZap/DataZap, QuintoAndar/OLX/ZAP, 27 state TJ databases, Receita Federal | No unified property identifier; heterogeneous website formats; anti-scraping measures; CAPTCHAs |

## Common Architecture

```
[Source Systems]  →  [Extraction]  →  [Staging]  →  [Transformation]  →  [Unified Data Layer]  →  [Serving]
```

### Typical Source Types (Recurring Across Verticals)

1. **ERP / Core Business Systems** -- structured data via REST APIs or direct database connections (TOTVS Protheus REST API, Guidewire, policy admin systems)
2. **Regulatory / Government APIs** -- ANM SIGMINE, SUSEP Open Data, CVM filings, PNCP/ComprasNet, Receita Federal CNPJ
3. **Third-Party Data Providers** -- credit bureaus (Serasa, Boa Vista), market data (B3, FipeZap), aggregation platforms (Gorila, SmartBrain, Pluggy)
4. **Unstructured Documents** -- PDFs, scanned images requiring OCR (editais, environmental licenses, apolices)
5. **IoT / Telemetry** -- equipment sensors (Cat Product Link, Komatsu KOMTRAX), environmental monitoring, dam instrumentation
6. **Web Sources** -- scraped data from leiloeiro websites, property listings, court record portals
7. **Communication Channels** -- WhatsApp Business, email, CRM interaction logs

### Normalization Strategies

- **Entity Resolution**: Canonical identifiers for entities that appear across systems (clients, properties, equipment, policies). Critical in auctions where matricula numbers are cartorio-specific with no unified property identifier.
- **Schema Mapping**: Source-specific schemas mapped to a canonical data model per vertical. Maintain mapping tables that handle format variations (date formats, currency representations, address normalization).
- **Temporal Alignment**: Harmonize data with different update frequencies (real-time telemetry vs. monthly regulatory filings vs. annual reports) into a consistent temporal model.
- **Data Quality Layer**: Completeness checks, range validation, cross-source reconciliation. Flag and quarantine records that fail quality rules rather than silently ingesting bad data.
- **Incremental Ingestion**: CDC (Change Data Capture) where available; timestamp-based polling otherwise. Full refreshes only for sources without reliable change tracking.

### Recommended Stack

| Component | Recommended Tools | Notes |
|-----------|------------------|-------|
| **Extraction - APIs** | Python connectors, Airbyte, custom REST clients | TOTVS Protheus REST, Gorila Connect API, Pluggy Open Finance API, SUSEP Open Data REST |
| **Extraction - Web** | Scrapy, Playwright/Puppeteer, rotating proxies | Essential for auctions (1,000+ sites); Apify marketplace has pre-built connectors for Caixa, Santander, OLX |
| **Extraction - IoT** | Azure IoT Hub, MQTT brokers | Mining telemetry: Cat Product Link, Komatsu KOMTRAX, OPC-UA |
| **Orchestration** | Apache Airflow, Prefect, Azure Data Factory | Schedule and monitor all extraction/transformation jobs |
| **Data Lake** | Azure Data Lake Storage Gen2, AWS S3 | Raw zone (immutable source copies) + curated zone (transformed) |
| **Data Warehouse** | Databricks, Azure Synapse, Snowflake | Unified analytics layer; Databricks aligns with Nexa Resources precedent in mining |
| **Search / Full-Text** | Elasticsearch, PostgreSQL full-text | Auctions: full-text search across edital content; Insurance: policy document search |
| **Caching** | Redis | High-frequency lookups (property valuations, real-time compliance checks) |
| **Visualization** | Power BI, custom dashboards (React) | Power BI strong in mining (Azure/TOTVS partnership); custom for auction map UIs |
| **Geospatial** | ArcGIS, QGIS, Mapbox, PostGIS | Mining: spatial analysis of concessions; Auctions: property geolocation visualization |

### Cloud Platform Preference

- **Azure**: Strong TOTVS partnership; preferred for mining and insurance verticals
- **AWS**: Broad ecosystem; viable for all verticals
- Both support the full stack above; choose based on client's existing cloud posture

## Implementation Considerations

### Data Governance
- LGPD compliance is mandatory across all verticals (fines up to 2% revenue / R$50M)
- Consent management especially critical for investment advisory (Pluggy Open Finance requires explicit client consent) and insurance (OPIN consent alignment)
- Data lineage tracking from source to derived analytics
- Role-based access controls per data sensitivity level

### Incremental Delivery
- Start with the 2-3 highest-value sources per vertical (not all 5-12 at once)
- Mining: ERP + mine planning + fleet management first
- Investment: platform data + consolidation tool + CRM first
- Insurance: policy admin + credit bureau + SUSEP first
- Auctions: top leiloeiro sites + Caixa API + FipeZap first
- Add remaining sources iteratively as value is proven

### Anti-Fragility
- Source systems change without notice (API deprecation, website redesign, regulatory portal updates)
- Build monitoring for extraction failures with automated alerts
- Maintain fallback extraction methods (e.g., manual CSV upload when API is down)
- Version all schema mappings; test transformations against historical data

## Estimated Investment

| Vertical | Typical First Project | Timeline | Scope |
|----------|----------------------|----------|-------|
| **Mining** | R$300K-R$700K | 12-16 weeks | ERP + FMS + mine planning integration with real-time dashboards |
| **Investment** | R$150K-R$300K | 8-12 weeks | Platform APIs + consolidation tools + CRM into unified reporting pipeline |
| **Insurance** | R$300K-R$600K | 4-6 months | Policy admin + credit bureaus + OPIN API gateway |
| **Auctions** | R$250K-R$400K | 3-4 months | 500+ leiloeiro sites scraped and normalized into unified search database |

## Cross-References

- Mining systems landscape: `kb/verticals/mining/tech-landscape.md`
- Investment integration points: `kb/verticals/investment-advisory/tech-landscape.md`
- Insurance ecosystem: `kb/verticals/insurance-surety/tech-landscape.md`
- Auctions data sources: `kb/verticals/auctions/tech-landscape.md`
- Built on by: [compliance-automation.md](compliance-automation.md), [predictive-models.md](predictive-models.md), [client-360.md](client-360.md)
