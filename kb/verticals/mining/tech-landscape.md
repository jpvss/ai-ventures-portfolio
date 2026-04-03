---
title: "Mining Consulting — Technology Landscape"
type: tech-landscape
vertical: mining
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [mining, technology, systems, apis, data-sources, TOTVS, Surpac, DISPATCH]
---

# Mining Consulting — Technology Landscape

## Common Client Systems

| System Type | Common Products | Market Position | Integration Method | Data Format |
|-------------|----------------|-----------------|-------------------|-------------|
| **ERP** | TOTVS Protheus | ~60% penetration in mid-market mining | REST API (Protheus REST API framework), Smart Analytics | Structured DB, REST JSON |
| **ERP** (alternative) | SAP Business One | Smaller share in mid-market | SAP APIs, BAPI | Structured DB |
| **Mine Planning** | GEOVIA Surpac (Dassault) | Leading mine planning software | File export (block models, designs) | DXF, CSV, proprietary formats |
| **Mine Planning** | Deswik | Growing adoption | File export, API | Proprietary, CSV |
| **Mine Planning** | Vulcan (Maptek) | Established player | File export | Proprietary formats |
| **Mine Planning** | Datamine | Alternative option | File export | Proprietary formats |
| **Fleet Management (FMS)** | Modular DISPATCH (Komatsu) | Major FMS provider | SQL databases, REST APIs, OPC-UA | SQL, real-time streams |
| **Fleet Management (FMS)** | Cat MineStar (Caterpillar) | Major FMS provider | SQL databases, REST APIs | SQL, real-time streams |
| **Fleet Management (FMS)** | Wenco | Alternative FMS | SQL, API | SQL |
| **Fleet Management (FMS)** | Hexagon Jigsaw | Growing player | SQL, REST API | SQL, real-time streams |
| **Environmental Monitoring** | Standalone sensors/spreadsheets | Most common in mid-market | Manual data entry, CSV exports | Spreadsheets, CSV |
| **Lab/LIMS** | Various LIMS systems | Separate from other systems | SQL, file export | Structured DB, CSV |

## Data Sources

### Public/Government APIs and Systems

| Source | Data Available | Access Method | Cost | Freshness |
|--------|---------------|--------------|------|-----------|
| **ANM SIGMINE** | Mining rights, concession areas, regulatory data | Shapefiles/KMZ downloads, new ArcGIS web APIs | Free | Updated periodically |
| **ANM PGRM** | CFEM/DIEF submission platform | Digital submission API (launched March 2025 by Serpro) | Free | Real-time |
| **ANM Cadastro Mineiro** | Mining title registry | Web portal | Free | Updated periodically |
| **ANM DIEF-CFEM** | CFEM payment records | Web portal, PGRM integration | Free | Monthly |
| **ANM SNISB** | Dam safety information | Data submission/query | Free | Real-time requirement |
| **IBAMA Portal Ecossistemas** | Environmental licensing data | Web portal | Free | Per submission |
| **SEMAD SLA (Minas Gerais)** | State environmental licensing | Digital system (since 2019) | Free | Real-time |
| **IBGE** | Geospatial and demographic data | Public APIs | Free | Varies |
| **ANA** | Hydrological data, water rights (outorga) | Public APIs | Free | Varies |

### Commercial Data Providers

| Provider | Data Available | Pricing Model | Integration |
|----------|---------------|--------------|-------------|
| **Jazida.com** | Commercial ANM data integration -- mining rights, CFEM data, regulatory status | Subscription | API platform |
| **Cat Product Link** (Caterpillar) | Equipment telemetry -- location, hours, fuel, diagnostics | Included with Cat equipment | REST API |
| **Komatsu KOMTRAX** | Equipment telemetry -- location, hours, fuel, diagnostics | Included with Komatsu equipment | REST API |

### Client Internal Data

Typical internal data sources we need access to during engagements:

- **NF-e (Notas Fiscais Eletronicas)**: Sales transaction data for CFEM calculation -- the critical data source
- **Production databases**: Tonnage, grade, destination, shift records
- **Geological databases**: Drilling data, assay results, block models, resource estimates
- **Maintenance records**: Work orders, parts inventory, equipment history
- **Environmental monitoring data**: Water quality, air quality, noise levels, dam instrumentation (piezometers, inclinometers)
- **Safety records**: Incident reports, near-misses, training logs, CIPAMIN minutes, PGR documentation
- **HR/training data**: NR-22 training completion, certifications
- **Financial data**: Revenue, costs, CFEM payments, tax records

## Integration Patterns

### Pattern 1: TOTVS Protheus Integration

**Source:** TOTVS Protheus ERP
**Method:** REST API (Protheus REST API framework)
**Challenges:** API maturity varies by Protheus version; some modules lack REST endpoints; Smart Analytics may require separate licensing
**Solution:** Use Protheus REST API for NF-e/sales data extraction; fall back to direct database access (SQL) for modules without API coverage; leverage Smart Analytics for built-in BI capabilities

### Pattern 2: FMS Data Extraction

**Source:** DISPATCH, MineStar, Wenco, Hexagon Jigsaw
**Method:** SQL databases (primary), REST APIs (where available), OPC-UA (for real-time streams)
**Challenges:** Each FMS has different data models; real-time vs. batch access trade-offs; historical data volumes can be massive
**Solution:** Build FMS-agnostic data abstraction layer; use SQL for historical analytics, OPC-UA for real-time dashboards; implement incremental extraction for large datasets

### Pattern 3: Mine Planning Data Integration

**Source:** Surpac, Deswik, Vulcan, Datamine
**Method:** File export (block models, pit designs, schedules)
**Challenges:** Proprietary file formats; large file sizes for block models; version control of geological models
**Solution:** Scheduled file export with parsing pipeline; convert to standardized format (CSV/Parquet) for analytics; maintain version history of block models

### Pattern 4: Environmental Sensor Integration

**Source:** Standalone environmental monitoring equipment (weather stations, water quality sensors, dam instrumentation)
**Method:** IoT protocols (MQTT, OPC-UA), serial connections, manual CSV uploads
**Challenges:** Diverse sensor manufacturers; connectivity in remote mine sites; data quality and calibration
**Solution:** Azure IoT Hub as central gateway; edge devices for connectivity gaps; automated data quality checks with anomaly detection

### Pattern 5: ANM Digital Systems Integration

**Source:** PGRM, SIGMINE, DIEF-CFEM
**Method:** Web APIs (PGRM), ArcGIS web APIs (SIGMINE), file downloads (shapefiles/KMZ)
**Challenges:** PGRM platform is new (March 2025) with evolving API documentation; SIGMINE data requires geospatial processing
**Solution:** PGRM API integration for CFEM/DIEF submission; ArcGIS/QGIS for SIGMINE spatial data; automated compliance submission workflows

## Recommended Tech Stack

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| **Cloud Platform** | Azure (primary) or AWS | Azure has strong TOTVS partnership; AWS as alternative for non-TOTVS shops |
| **Data Platform** | Databricks or Azure Synapse | Databricks proven in mining (Nexa Resources reference); Synapse for Azure-native shops |
| **Data Ingestion** | Azure Data Factory | Managed ETL/ELT with connectors for SQL, REST, file systems |
| **IoT Integration** | Azure IoT Hub | Sensor data from environmental monitoring, dam instrumentation |
| **Visualization** | Power BI | Strong TOTVS integration, widely adopted in Brazilian mid-market |
| **Spatial Analysis** | ArcGIS or QGIS | Mining requires geospatial capabilities; ArcGIS for enterprise, QGIS for cost-sensitive |
| **ML/AI** | Databricks ML or Azure ML | Predictive maintenance, grade optimization, blending models |
| **Real-Time Processing** | Azure Stream Analytics or Spark Streaming | Fleet real-time dashboards, dam safety monitoring |
| **Storage** | Azure Data Lake Storage Gen2 | Scalable storage for geological data, telemetry, production history |
| **API Layer** | Azure API Management | Expose analytics to client systems, PGRM integration |

## Key Technical Challenges

1. **TOTVS Protheus API maturity**: REST API coverage varies significantly by version and module. Older installations may require direct database access, which carries upgrade risk.

2. **FMS data heterogeneity**: Each fleet management system (DISPATCH, MineStar, Wenco, Hexagon) has a different data model. Building FMS-agnostic analytics requires a robust abstraction layer.

3. **Mine site connectivity**: Remote mine sites often have limited internet bandwidth. IoT and real-time analytics may require edge computing solutions.

4. **Geological data complexity**: Block models, drilling data, and assay results use specialized formats and coordinate systems. Geospatial expertise is required for integration.

5. **PGRM platform maturity**: Launched March 2025 by Serpro, the PGRM platform for CFEM/DIEF is still evolving. API documentation and stability may require adaptive integration approaches.

6. **Data volumes**: Mining operations generate massive data volumes from FMS (truck positions every few seconds), sensors (continuous monitoring), and geological databases (millions of block model cells). Architecture must handle terabyte-scale datasets.

7. **Regulatory change velocity**: ANM, IBAMA, and labor regulations (NR-22) evolve frequently. Solutions must be designed for configuration-driven rule changes, not hardcoded compliance logic.

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
