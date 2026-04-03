---
title: "Education & HR — Tech Landscape"
type: tech-landscape
vertical: education-hr
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [education-hr, tech-landscape, APIs, data-sources, RAIS, CAGED, CBO, INEP, stack]
---

# Education & HR — Tech Landscape

## Public Data Sources

### RAIS (Relação Anual de Informações Sociais)

| Attribute | Details |
|-----------|---------|
| **Source** | Ministério do Trabalho e Emprego (MTE) |
| **Coverage** | All formal employment relationships in Brazil (~50M records/year) |
| **Update frequency** | Annual (reference year data published ~12-18 months later) |
| **Access** | Public microdata via Portal Emprega Brasil; aggregated data freely available |
| **Format** | CSV microdata files; fixed-width legacy format |
| **Key fields** | CNAE (industry), CBO (occupation), municipality, salary range, education level, age, gender, admission/termination dates |
| **Limitations** | Annual lag means data is 12-18 months old; excludes informal workers (~40% of workforce); microdata access requires formal request |
| **AI applications** | Salary benchmarking by occupation/region, labor market trend analysis, skills demand forecasting, employer intelligence |
| **Integration approach** | Annual bulk load into data warehouse; dbt models for transformation; occupation-level aggregations for API |

### CAGED (Cadastro Geral de Empregados e Desempregados)

| Attribute | Details |
|-----------|---------|
| **Source** | MTE (via eSocial since 2020) |
| **Coverage** | Monthly admissions and terminations in formal employment |
| **Update frequency** | Monthly (published ~1 month after reference period) |
| **Access** | Public data via Portal Emprega Brasil; Novo CAGED since Jan 2020 |
| **Format** | CSV; API access via Portal Emprega Brasil |
| **Key fields** | CNAE, CBO, municipality, salary, admission/termination type, education level |
| **Limitations** | Only flows (new hires/terminations), not stock; Novo CAGED methodology change in 2020 creates discontinuity |
| **AI applications** | Near-real-time labor market signals, hiring trend detection, seasonal patterns, industry health indicators |
| **Integration approach** | Monthly automated ingestion via API/download; append to time-series data warehouse |

### CBO (Classificação Brasileira de Ocupações)

| Attribute | Details |
|-----------|---------|
| **Source** | MTE |
| **Coverage** | 2,500+ occupation codes with descriptions, activities, competencies |
| **Update frequency** | Infrequent (major revisions every 5-10 years; minor updates ongoing) |
| **Access** | Public via MTE website; PDF and web format |
| **Format** | Structured web pages; no official API (requires scraping or manual extraction) |
| **Key fields** | Occupation code, title, synonyms, description, main activities, required training, working conditions, related occupations |
| **Limitations** | No official API; some occupations are outdated (does not reflect emerging roles like "prompt engineer"); update cycle is slow |
| **AI applications** | Skills taxonomy backbone, occupation classification, career path mapping, competency framework |
| **Integration approach** | One-time extraction + LLM-assisted structuring into graph database; periodic update checks |

### INEP Data (Education Statistics)

| Dataset | Coverage | AI Application |
|---------|----------|---------------|
| **Censo da Educação Superior** | All higher education institutions, courses, enrollments, graduates | Education-to-employment correlation; program quality assessment |
| **ENEM** | National exam scores by subject, school, region | Student skill assessment benchmark; institutional quality proxy |
| **IDEB** | K-12 school quality index | Regional education quality mapping |
| **Censo Escolar** | K-12 school infrastructure, enrollment, teachers | Education ecosystem mapping |

**Access**: Public microdata via INEP portal; annual publication
**Format**: CSV microdata; documentation in Portuguese
**Integration approach**: Annual bulk load; join with RAIS/CBO for education-to-employment analysis

### Portal Emprega Brasil

| Attribute | Details |
|-----------|---------|
| **Source** | MTE/SINE |
| **Coverage** | Public job listings via SINE network; worker registration; employment services |
| **Access** | API available (gov.br integration) |
| **AI applications** | Public job market intelligence; SINE candidate pool for matching; integration with employment agency systems |
| **Integration approach** | REST API client; real-time or daily sync for job listings |

## Commercial Data Sources

### Job Posting Platforms

| Platform | Data Available | Access Method | Volume | Notes |
|----------|---------------|---------------|--------|-------|
| **Gupy** | Job postings, requirements, company info | Web scraping (no public API for third parties) | 50K+ active postings | Largest ATS in Brazil; postings reflect real hiring intent |
| **Catho** | Job postings, salary ranges, candidate profiles | API (partner access); web scraping | 100K+ active postings | Massive but declining relevance |
| **InfoJobs** | Job postings, company reviews | Web scraping | 50K+ active postings | Indeed-owned; good for operational roles |
| **LinkedIn Brazil** | Job postings, skills data, company info | LinkedIn API (limited); scraping (risky — anti-bot) | 200K+ active postings | Best for white-collar/tech roles; API restrictions increasing |
| **Glassdoor BR** | Salary data, company reviews, interview experiences | Web scraping | Limited but growing | Salary data is self-reported; useful as secondary source |
| **Vagas.com** | Job postings, candidate database | Web scraping | 30K+ active postings | Long-standing Brazilian job board |

### Salary Surveys

| Source | Coverage | Access | Notes |
|--------|----------|--------|-------|
| **Robert Half Salary Guide** | White-collar roles by function, seniority, city | Annual publication (PDF); subscription for detailed data | Most cited salary benchmark in Brazil |
| **Michael Page Salary Survey** | Management and specialist roles | Annual publication | Good for senior roles |
| **Glassdoor BR** | Self-reported salaries by company, role | API/scraping | Large volume but self-reported bias |
| **RAIS (public)** | Formal employment salaries by CBO/region | Free microdata | Official data; 12-18 month lag |

## Common Client Tech Stacks

### Mid-Market ATS Platform (Typical)

```
Frontend: React/Vue.js
Backend: Node.js or Ruby on Rails or Python/Django
Database: PostgreSQL or MySQL
Search: Elasticsearch (for job/candidate search)
Storage: AWS S3 / GCP Cloud Storage
Infrastructure: AWS or GCP (less commonly Azure in Brazil)
CI/CD: GitHub Actions or GitLab CI
Monitoring: Datadog or New Relic (if mature)
```

**Integration points for our solutions**:
- REST API webhook callbacks for screening results
- Database read access for training data extraction
- Elasticsearch integration for enhanced search
- S3/GCS access for CV file processing

### Mid-Market EdTech/Bootcamp (Typical)

```
LMS: Custom (Rails/Django) or Canvas/Moodle
Frontend: React/Next.js
Backend: Rails or Node.js
Database: PostgreSQL
Content delivery: CDN + video platform (Vimeo/YouTube/custom)
Assessment: Custom quiz engine or third-party (HackerRank for coding)
Analytics: Google Analytics + custom dashboards (Metabase/Redash)
```

**Integration points**: LMS API for skills extraction; assessment data for readiness scoring; student profiles for career matching

### Outplacement Consultancy (Typical)

```
CRM: Salesforce or Pipedrive or custom spreadsheets
Document management: Google Drive / SharePoint
CV storage: File folders (unstructured)
Communication: WhatsApp Business + email
Scheduling: Calendly or custom
Analytics: Spreadsheets (Excel/Google Sheets)
```

**Integration points**: Google Drive API for CV ingestion; CRM API for candidate tracking; low-tech environment means we often provide the primary data infrastructure

## Recommended Solution Stack (JP Ventures)

### Core Infrastructure

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| **Compute** | AWS (primary) or GCP | Most common in Brazilian market; client familiarity |
| **Database** | PostgreSQL + pgvector | Relational + vector search in one database; reduces complexity |
| **Search** | Elasticsearch or OpenSearch | Full-text search for JDs/CVs; faceted search for dashboards |
| **Data warehouse** | PostgreSQL + dbt or BigQuery | dbt for transformation; BQ if client already on GCP |
| **Message queue** | Redis/BullMQ or SQS | Async CV processing; job matching pipelines |
| **Object storage** | S3 / GCS | CV files, parsed outputs, model artifacts |
| **Container orchestration** | ECS Fargate or Cloud Run | Serverless containers; no cluster management overhead |

### AI/ML Layer

| Component | Technology | Rationale |
|-----------|-----------|-----------|
| **LLM (CV parsing, rewriting)** | Claude API (primary), GPT-4 (secondary) | Best Portuguese quality; structured output via tool use |
| **Embeddings** | multilingual-e5-large or text-embedding-3-small | Multilingual embeddings for Portuguese CV/JD semantic matching |
| **Vector store** | pgvector (if < 1M vectors) or Pinecone/Qdrant | pgvector keeps stack simple; scale to dedicated vector DB if needed |
| **ML training** | scikit-learn / XGBoost (tabular); PyTorch (if deep learning needed) | Start simple with gradient boosting for scoring models |
| **Model serving** | FastAPI + Docker | Lightweight, high-performance Python API |
| **Experiment tracking** | MLflow or Weights & Biases | Track model versions, metrics, hyperparameters |
| **Bias auditing** | Fairlearn + custom pipeline | Open-source fairness metrics; required for LGPD compliance |
| **Explainability** | SHAP + custom NL explanation generator | Feature attribution + human-readable explanations |

### Application Layer

| Component | Technology | Rationale |
|-----------|-----------|-----------|
| **API gateway** | Kong or AWS API Gateway | Rate limiting, auth, monitoring |
| **Authentication** | OAuth2 + JWT | Standard; compatible with client SSO |
| **Dashboard** | Next.js + Tailwind (custom) or Metabase (quick analytics) | Custom for client-facing; Metabase for internal analytics |
| **Monitoring** | Prometheus + Grafana or Datadog | Model performance + system health |
| **Alerting** | PagerDuty or Slack webhooks | Drift detection, bias threshold alerts |

### Data Pipeline Architecture

```
Data Sources                          Processing                        Storage & Serving
─────────────────                     ──────────────                    ──────────────────
RAIS/CAGED (bulk CSV)     ─┐
CBO (scraped/extracted)   ─┤         ┌─────────────┐                 ┌──────────────┐
Job postings (scraped)    ─┼────────►│  ETL Layer   │────────────────►│  PostgreSQL   │
Portal Emprega (API)      ─┤         │  (Python +   │                 │  + pgvector   │
Client CVs (S3/API)       ─┤         │  dbt)        │                 └──────┬───────┘
Client JDs (S3/API)       ─┤         └─────────────┘                        │
eSocial events (XML)      ─┘                                                ▼
                                     ┌─────────────┐                 ┌──────────────┐
                                     │  ML Pipeline │◄───────────────│  Feature      │
                                     │  (Training)  │                │  Store        │
                                     └──────┬──────┘                 └──────────────┘
                                            │
                                            ▼
                                     ┌─────────────┐                 ┌──────────────┐
                                     │  Model       │────────────────►│  REST API    │
                                     │  Serving     │                 │  (FastAPI)   │
                                     │  (FastAPI)   │                 └──────────────┘
                                     └─────────────┘
```

## Integration Patterns

### Pattern 1: ATS Webhook Integration
Client ATS sends new application via webhook → Our API processes CV → Returns structured profile + match score + explanation → Client ATS displays results to recruiter

### Pattern 2: Batch CV Processing
Client uploads batch of CVs (S3 bucket or SFTP) → Processing queue picks up → LLM extraction → Scoring → Results written to output bucket + webhook notification

### Pattern 3: Dashboard Embedding
Our analytics dashboard embedded in client application via iframe or React component → OAuth2 SSO → Real-time data from shared database

### Pattern 4: Public Data Enrichment
Client provides occupation codes or candidate profiles → Our API enriches with RAIS salary data, CBO competencies, market demand signals → Returns enriched profiles

## Technical Risks and Mitigations

| Risk | Probability | Mitigation |
|------|------------|------------|
| LLM Portuguese quality degrades on edge cases (informal CVs, mixed language) | Medium | Fine-tune extraction prompts on Brazilian CV corpus; fallback to rule-based parsing for structured sections |
| Job posting scraping blocked by platforms | High | Rotate proxies; respect robots.txt; build relationships for API access; cache aggressively; use Portal Emprega Brasil as stable fallback |
| CBO taxonomy outdated for emerging roles | Medium | Extend CBO with custom occupation nodes; detect emerging job titles from posting analysis; flag for manual review |
| pgvector performance at scale (>1M vectors) | Low-Medium | Monitor query latency; migration path to Qdrant/Pinecone if needed; partition by client |
| RAIS data lag (12-18 months) makes models stale | Medium | Supplement with CAGED (monthly) and live job postings (daily) for trend signals; RAIS provides structural baseline, not real-time signal |
| Client data quality too poor for ML | Medium-High | Include data quality assessment in diagnostic; recommend data collection phase before ML if needed; start with rule-based models |

## cv10x Component Reuse

The active cv10x project provides production-tested components directly applicable to client engagements:

| Component | cv10x Status | Client Reuse Potential |
|-----------|-------------|----------------------|
| CV parsing pipeline (PDF/DOCX → JSON) | Production | Direct reuse; 40-50% of CV Intelligence Platform |
| Skills extraction (free text → structured tags) | Production | Direct reuse; foundation for matching engine |
| ATS keyword analysis | Production | Reusable for ATS Screening API JD parsing |
| Quality scoring (CV completeness, impact language) | Production | Reusable with calibration per client |
| CBO taxonomy integration | In development | Foundation for all skills-based solutions |
| Job posting scraper framework | In development | Reusable for Talent Marketplace Intelligence |

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
