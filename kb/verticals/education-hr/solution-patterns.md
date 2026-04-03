---
title: "Education & HR — Solution Patterns"
type: solution-patterns
vertical: education-hr
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [education-hr, solutions, technical, patterns, cv-intelligence, ats, matching, skills-gap]
---

# Education & HR — Solution Patterns

## Solution Projects

### Project 1: CV Intelligence Platform (R$60K-R$150K)

**Problem**: CV review is the bottleneck for outplacement firms and recruitment agencies. Each CV takes 2-4 hours for a senior consultant to analyze, rewrite, and optimize. At 5 CVs/day capacity, firms cannot scale beyond their current headcount.

**Target clients**: Outplacement consultancies, career coaching firms, recruitment agencies

**Solution Architecture**:
```
CV upload (PDF/DOCX) → Document parsing (OCR + LLM extraction)
→ Structured profile (skills, experience, education, achievements)
→ Skills mapping (CBO taxonomy alignment)
→ Quality scoring (completeness, ATS compatibility, impact language)
→ Optimization suggestions (keyword gaps, achievement rewriting, format)
→ Rewritten CV output (multiple formats, ATS-optimized)
```

**Technical Components**:
- **Document parser**: PDF/DOCX ingestion with layout-aware extraction (Azure AI Document Intelligence or custom pipeline)
- **LLM extraction**: GPT-4/Claude for unstructured text → structured JSON (skills, experience periods, education, certifications)
- **Skills normalizer**: Map free-text skills to CBO taxonomy codes + custom client taxonomy
- **Quality scorer**: Multi-factor scoring: ATS keyword match rate, achievement quantification, format compliance, section completeness
- **Optimization engine**: LLM-powered rewriting with style transfer (formal/informal, industry-specific language)
- **Output generator**: Multi-format CV generation (PDF, DOCX, LinkedIn-optimized text)

**cv10x Reuse**: Core CV parsing, skills extraction, and quality scoring components from the active cv10x project are directly applicable. Estimated 40-50% code reuse, reducing delivery from 3 months to 6-8 weeks.

**Cross-Vertical Pattern**: See `kb/patterns/document-intelligence.md` — same parsing pipeline as edital analysis (auctions) and apólice parsing (insurance)

**Estimated Effort**: R$60K-R$150K, 6-12 weeks
**Expected ROI**: 2-4 hrs per CV → 30 seconds automated analysis + 15 min human refinement. 10x throughput increase per consultant.

### Project 2: ATS Screening API (R$100K-R$250K)

**Problem**: Mid-market ATS platforms use keyword matching that misses 40%+ of qualified candidates. A candidate writing "gestão de equipes" gets rejected when the JD requires "liderança." Semantic understanding is needed, not string matching.

**Target clients**: HRTech/ATS platforms, corporate HR departments

**Solution Architecture**:
```
Job Description → JD Parser (requirements extraction with weights)
                                    ↓
Candidate CV → CV Parser → Structured Profile
                                    ↓
              Semantic Matching Engine (embeddings + rule-based)
                                    ↓
              Ranked Candidate List + Match Explanations
                                    ↓
              API Response (REST/GraphQL, webhook callbacks)
```

**Technical Components**:
- **JD parser**: LLM extraction of required skills (hard/soft), experience level, education, certifications, with importance weights
- **Embedding engine**: Sentence-level embeddings (multilingual-e5-large or custom fine-tuned) for semantic similarity
- **Skills graph**: CBO-based skills taxonomy with synonyms, hypernyms, and related skills (e.g., "liderança" ↔ "gestão de equipes" ↔ "coordenação")
- **Matching algorithm**: Hybrid approach — embedding cosine similarity + taxonomy graph distance + rule-based hard filters (location, salary, availability)
- **Scoring model**: Weighted composite score with configurable weights per client/JD
- **Explainability layer**: For each match score, generate human-readable explanation of why candidate matched/didn't match each requirement
- **API layer**: REST API with OAuth2, rate limiting, webhook callbacks for async processing

**Bias mitigation**: 
- Remove name, age, gender, photo before matching (blind screening mode)
- Demographic parity testing on scoring distribution
- Regular bias audits with client data

**Cross-Vertical Pattern**: See `kb/patterns/scoring-engines.md` — same multi-factor scoring approach as investment scoring (auctions) and risk scoring (insurance)

**Estimated Effort**: R$100K-R$250K, 3-5 months
**Expected ROI**: Matching accuracy from ~50% (keyword) to 85%+ (semantic). 3x reduction in time-to-shortlist. 40% reduction in qualified candidate rejection.

### Project 3: Employability Assessment Module (R$80K-R$200K)

**Problem**: Bootcamps and training programs cannot objectively measure whether students are ready for employment. Completion certificates prove attendance, not capability. Students lack actionable feedback on what skills to develop.

**Target clients**: Bootcamps, professional training programs, universities with career services

**Solution Architecture**:
```
Student Profile (skills, projects, assessments)
→ Skills Mapper (CBO + live job market alignment)
→ Gap Analyzer (student skills vs. market requirements)
→ Readiness Scorer (composite employment readiness score)
→ Recommendation Engine (targeted skill development paths)
→ Dashboard (student view + institution view + employer view)
```

**Technical Components**:
- **Skills inventory**: Extract skills from student projects, assessments, course completions; map to CBO taxonomy
- **Market requirements engine**: Aggregate requirements from 500K+ live job postings (Gupy, Catho, InfoJobs, LinkedIn) by occupation and seniority
- **Gap analyzer**: Compare student skill set against target occupation requirements; identify critical gaps and nice-to-have gaps
- **Readiness scorer**: ML model predicting employment probability based on skills, portfolio quality, market demand — trained on historical placement data (cold-start with RAIS employment rates by CBO)
- **Recommendation engine**: Prioritized list of skills/projects/certifications to close gaps, with estimated time investment
- **Outcome tracker**: Post-graduation employment tracking integration (LinkedIn API, student surveys, employer confirmation)

**Data sources**: RAIS/CAGED (employment rates by occupation), CBO (required competencies), live job postings (current market demands), INEP (education quality benchmarks)

**Cross-Vertical Pattern**: See `kb/patterns/scoring-engines.md` and `kb/patterns/data-integration.md`

**Estimated Effort**: R$80K-R$200K, 2-4 months
**Expected ROI**: Bootcamps can demonstrate data-backed employment outcomes (marketing advantage). Students get actionable development plans. Employers get pre-validated candidates.

### Project 4: Talent Marketplace Intelligence (R$100K-R$250K)

**Problem**: Talent marketplaces and recruitment platforms lack real-time labor market intelligence. They cannot answer: "What skills are in demand in São Paulo this quarter?", "What salary should we offer for a mid-level data engineer?", "Which industries are hiring fastest?"

**Target clients**: Talent marketplaces, recruitment platforms, workforce planning teams

**Solution Architecture**:
```
Data Ingestion Layer:
  - RAIS/CAGED (monthly employment flows)
  - CBO (occupation taxonomy)
  - Job posting scrapers (Gupy, Catho, InfoJobs, LinkedIn)
  - Salary survey data (Robert Half, Michael Page, Glassdoor BR)
→ ETL Pipeline (normalization, deduplication, CBO mapping)
→ Analytics Data Warehouse (PostgreSQL + dbt)
→ Intelligence Layer:
  - Demand trend analysis by skill/occupation/region
  - Salary benchmarking engine
  - Supply-demand gap identification
  - Emerging skills detection
→ API + Dashboard
```

**Technical Components**:
- **Multi-source ingestion**: Scrapers for job boards + RAIS/CAGED bulk data loaders + API integrations
- **Normalization engine**: Map heterogeneous job titles/skills to CBO taxonomy (LLM-assisted classification)
- **Trend analysis**: Time-series analysis of skill demand, salary movements, hiring volumes by sector/region
- **Salary model**: Regression model predicting salary by occupation, experience, region, industry, company size — trained on RAIS + job posting data
- **Supply-demand scorer**: Compare candidate supply (job seekers by skill) against demand (open positions by skill) to identify shortages and surpluses
- **Emerging skills detector**: NLP analysis of new terms appearing in job postings not yet in CBO taxonomy

**Cross-Vertical Pattern**: See `kb/patterns/data-integration.md` — same multi-source aggregation approach as auction data aggregation

**Estimated Effort**: R$100K-R$250K, 3-5 months
**Expected ROI**: Clients gain market intelligence that was previously only available to large enterprises with dedicated research teams. Enables data-driven pricing, hiring strategy, and product development.

### Project 5: Skills Gap Analytics (R$80K-R$200K)

**Problem**: HR departments and L&D teams cannot quantify workforce skills gaps. They know "we need more data skills" but cannot say "42% of our analysts lack SQL proficiency, and closing this gap would reduce report turnaround by 30%."

**Target clients**: Corporate HR/L&D departments, People Analytics teams, HR consulting firms

**Solution Architecture**:
```
Workforce Data (eSocial, HRIS, LMS, performance reviews)
→ Current Skills Mapper (extract + classify existing workforce competencies)
→ Target Skills Definer (industry benchmarks + strategic goals + CBO)
→ Gap Quantifier (individual + team + organization level gaps)
→ Impact Modeler (link gaps to business outcomes)
→ Training Recommender (prioritized development paths with ROI estimates)
→ Tracking Dashboard (gap closure over time)
```

**Technical Components**:
- **Skills extractor**: NLP pipeline to extract skills from performance reviews, project assignments, LMS completions, self-assessments
- **Skills taxonomy**: CBO-based + client-custom taxonomy with proficiency levels (beginner/intermediate/advanced/expert)
- **Benchmarking engine**: Compare workforce skills distribution against industry peers (RAIS data) and best-in-class organizations
- **Gap quantifier**: Per-employee, per-team, and per-organization skills gap matrices with severity scoring
- **Impact model**: Correlate skills gaps with business KPIs (productivity, quality, customer satisfaction) using historical data
- **Training recommender**: Match gaps to available training resources (internal LMS, external courses, certifications) with time/cost estimates
- **ROI calculator**: Project business impact of closing specific gaps — essential for L&D budget justification

**Cross-Vertical Pattern**: See `kb/patterns/scoring-engines.md`

**Estimated Effort**: R$80K-R$200K, 2-4 months
**Expected ROI**: Quantified skills gaps enable targeted L&D investment. Typical finding: 30-40% of training budget is spent on non-critical skills.

## Reusable Technical Patterns

### Pattern A: CV/Document Intelligence Pipeline

Shared component across CV Intelligence Platform, ATS Screening API, and Employability Assessment Module.

```
Input (PDF/DOCX/Image) → Layout Detection → Text Extraction → LLM Structuring → Validation → Structured Output (JSON)
```

**Reuse from cv10x**: The cv10x project has a production-tested CV parsing pipeline that handles Brazilian CV formats (Lattes, Europass BR, free-form). This component is directly deployable in client engagements.

**Cross-vertical**: Same pattern as edital parsing (auctions), apólice analysis (insurance), environmental license parsing (mining).

### Pattern B: Skills Taxonomy & Matching Engine

Foundation for all 5 solution projects. Based on CBO taxonomy with extensions.

```
CBO Base Taxonomy (2,500 occupations)
→ Skills Ontology (extracted competencies per occupation)
→ Synonym/Alias Layer (regional variations, English equivalents)
→ Embedding Index (semantic search over skills)
→ Graph Structure (related skills, prerequisite chains, career paths)
```

### Pattern C: Public Data Integration Layer

Reusable connectors for Brazilian employment/education public data.

| Data Source | Format | Update Frequency | Connector Type |
|-------------|--------|-----------------|----------------|
| RAIS | CSV/microdata | Annual | Bulk loader + incremental parser |
| CAGED | CSV | Monthly | Automated monthly ingestion |
| CBO | Web/PDF | Infrequent | One-time load + update monitor |
| INEP (Censo) | CSV/microdata | Annual | Bulk loader |
| Portal Emprega Brasil | API | Real-time | REST API client |
| eSocial events | XML | Real-time | XML parser + event processor |

### Pattern D: Bias Audit Pipeline

Required for all AI recruitment systems (regulatory compliance + ethical commitment).

```
Scoring Model Output → Demographic Split (protected classes)
→ Disparate Impact Analysis (4/5ths rule)
→ Equalized Odds Check → Calibration Analysis
→ Audit Report (pass/fail with recommendations)
→ Automated Alerts (if bias threshold exceeded)
```

### Pattern E: Explainability Layer

Required by LGPD Art. 20 for automated decisions affecting candidates.

```
Model Prediction → SHAP/LIME Feature Attribution
→ Natural Language Explanation Generator (LLM)
→ Candidate-Facing Explanation (simplified)
→ Auditor-Facing Explanation (detailed with feature weights)
```

## Solution-to-Pattern Matrix

| Solution Project | Pattern A (Doc Intel) | Pattern B (Skills) | Pattern C (Public Data) | Pattern D (Bias) | Pattern E (Explain) |
|-----------------|----------------------|--------------------|-----------------------|-------------------|---------------------|
| CV Intelligence Platform | Primary | Primary | Secondary | Required | Required |
| ATS Screening API | Primary | Primary | Secondary | Critical | Critical |
| Employability Assessment | Secondary | Primary | Primary | Required | Required |
| Talent Marketplace Intel | - | Primary | Primary | - | - |
| Skills Gap Analytics | Secondary | Primary | Primary | Required | Required |

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
