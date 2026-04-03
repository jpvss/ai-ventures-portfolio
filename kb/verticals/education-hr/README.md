---
title: "Education & HR — Overview"
type: README
vertical: education-hr
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [education-hr, overview, hrtech, edtech, recruitment, cv-optimization]
---

# Education & HR (Educação e Recursos Humanos)

## Summary

Brazil's HR tech market exceeds R$4B and grows 15-20% YoY, while EdTech surpasses R$10B. Despite this scale, the mid-market segment — outplacement consultancies, ATS platforms, bootcamps, and employment agencies — remains stuck with manual processes and primitive automation. CV review averages 2-4 hours per candidate, ATS keyword matching misses qualified talent, bootcamps cannot measure employment readiness, and outplacement firms cannot scale their services beyond a handful of simultaneous clients.

The convergence of GenAI capabilities (LLM-based CV analysis, agent-driven recruitment pipelines, ML candidate-job matching) with rich public data sources (RAIS/CAGED formal employment data, CBO occupation taxonomies, INEP education census) creates an unprecedented opportunity. Mid-market players need data infrastructure to compete with well-funded incumbents like Gupy, but lack the AI/ML expertise to build it themselves.

JP Ventures positions as the AI-native data infrastructure partner for Education & HR mid-market companies. Our engagement arc — paid diagnostic through implementation to retainer — delivers quantified ROI by automating CV intelligence, recruitment screening, employability assessment, and skills gap analytics. Our active cv10x project provides direct domain expertise and reusable components for this vertical.

## Key Metrics

| Metric | Value | Source |
|--------|-------|--------|
| HR Tech Market Size (Brazil) | R$4B+ | raw/industry-templates.md |
| EdTech Market Size (Brazil) | R$10B+ | raw/industry-templates.md |
| HR Tech Growth Rate | 15-20% YoY | raw/industry-templates.md |
| Manual CV Review Time | 2-4 hours per candidate | raw/industry-templates.md |
| ATS Keyword Match Accuracy | ~40-60% (primitive matching) | Industry estimates |
| Formal Employment Records (RAIS) | 50M+ records annually | MTE/RAIS |
| CBO Occupation Codes | 2,500+ occupations with competency maps | MTE/CBO |
| Mid-Market Target Count | 500+ companies (outplacement, ATS, edtech, agencies) | raw/industry-templates.md |
| Avg. Diagnostic Price | R$25K-R$60K | raw/industry-templates.md |
| 12-Month Portfolio Value | R$400K-R$1.05M per client | raw/industry-templates.md |
| Ongoing Retainer | R$10K-R$30K/mo | raw/industry-templates.md |

## Our Positioning

JP Ventures differentiates in the Education & HR vertical by combining deep domain knowledge (active cv10x project) with cross-vertical AI patterns. While competitors like Gupy and Revelo build monolithic platforms, we deliver modular data infrastructure that mid-market players can integrate into their existing workflows.

Our key advantages:
- **Active domain project (cv10x)**: Hands-on experience building CV optimization and career tools gives us production-tested components and genuine domain credibility
- **Cross-vertical pattern reuse**: The same document intelligence pipeline that parses CVs also handles editais in auctions and apolices in insurance; scoring engines transfer directly from property valuation to candidate matching
- **Public data integration expertise**: We specialize in connecting RAIS/CAGED employment data, CBO taxonomies, and INEP education data into unified intelligence layers — data that mid-market players know exists but cannot operationalize
- **Quantified ROI delivery**: Every engagement targets measurable outcomes (2-4 hrs to 30 sec CV analysis, 40% to 85%+ matching accuracy, manual screening to automated pipelines)

## GenAI Leverage Map

### Document Intelligence (LLM)

| Document Type | Current Process | GenAI Solution | Est. ROI |
|---------------|----------------|----------------|----------|
| CV/Resume parsing | Manual review 2-4 hrs per candidate, subjective assessment | LLM extraction of skills, experience, education with structured scoring | 95%+ time reduction per CV |
| Job description analysis | Recruiters manually interpret requirements, inconsistent criteria | Automated extraction of required/desired skills, seniority level, culture fit signals | Standardized matching criteria across all JDs |
| Training certificates/diplomas | Manual verification of credentials, cross-reference with institutions | OCR + LLM validation of credentials, automated institutional verification | Hours to seconds; enables batch verification |
| Employee performance reviews | HR reads unstructured text to identify patterns and growth areas | Structured extraction of competencies, gaps, and development recommendations | 10x more reviews analyzed per HR analyst |

### Agentic Workflows

| Workflow | Steps Automated | Human-in-Loop Points | Tools Used |
|----------|----------------|---------------------|------------|
| CV screening agent | Ingest CV -> extract structured data -> match against JD requirements -> score candidate -> generate shortlist memo | Recruiter reviews shortlist and final selection | LLM extraction, skills taxonomy matcher, scoring model, memo generator |
| Recruitment pipeline agent | Post JD to multiple channels -> collect applications -> screen CVs -> schedule interviews -> track pipeline status | Hiring manager approves shortlist; interviewer provides feedback | Multi-channel API, CV parser, scheduling API, CRM integration |
| Employability assessment agent | Analyze student portfolio -> map skills to CBO taxonomy -> compare against job market requirements -> generate readiness report | Career counselor reviews report with student | Portfolio analyzer, CBO API, RAIS/CAGED data, report generator |
| Skills gap analytics agent | Aggregate workforce data -> map current competencies -> compare against industry trends -> recommend training paths | HR director validates priorities and budget allocation | RAIS data, CBO taxonomy, training catalog, recommendation engine |

### Knowledge Retrieval (RAG)

| Corpus | Est. Size | Use Case | Primary Users |
|--------|-----------|----------|---------------|
| CBO occupation taxonomy | 2,500+ occupations with competencies | Map candidate skills to standardized occupations, identify transferable skills | CV analysis engine, career counselors |
| CLT labor regulations | ~900 articles + commentary | Answer employment law questions, validate contract terms, compliance checking | HR platforms, legal teams |
| RAIS/CAGED employment data | 50M+ annual records | Labor market trends by occupation, region, industry; salary benchmarks | Analytics dashboards, career tools |
| BNCC/MEC education standards | ~600 competencies across education levels | Map curriculum to employability skills, assess program alignment with market needs | EdTech platforms, bootcamps |
| Job posting corpus (Gupy/Catho/InfoJobs) | 500K+ active postings | Real-time skill demand analysis, salary benchmarking, JD template generation | Recruitment platforms, career tools |

### Predictive Models (ML)

| Prediction | Data Available | Cold-Start Strategy | Business Impact |
|------------|---------------|---------------------|-----------------|
| Candidate-job match score | CV data, JD requirements, historical hiring outcomes | Start with CBO skills taxonomy + keyword overlap; refine with client hiring data | 2-3x improvement in shortlist quality; reduces time-to-hire by 40% |
| Employment readiness score | Student skills, portfolio, CBO requirements, RAIS employment rates | Rule-based model from CBO + RAIS data; transition to ML with bootcamp outcomes | Bootcamps can demonstrate employment outcomes; students get actionable gaps |
| Salary prediction | RAIS salary data, occupation, experience, region, industry | RAIS public data for top 50 occupations; expand with client data | Enables fair offer generation; reduces salary negotiation friction |
| Attrition risk | Employee tenure, performance data, industry benchmarks | Industry averages from RAIS turnover data; personalize per client | Early warning for flight risk; targeted retention interventions |

## Decision-Maker Personas

### 1. Outplacement/Recolocação Consultancy Director
- **Profile**: Manages 50-200 active candidates, team of 5-15 career coaches
- **Pain**: Each CV review takes 2-4 hours, coaches are bottleneck, cannot scale beyond current capacity without hiring
- **Hook**: "Your coaches review 5 CVs per day. Our AI reviews 500 and flags the 20 that need human attention"
- **Buying trigger**: Demo showing CV analysis quality matching senior coach output; capacity math showing 10x throughput
- **Budget**: R$60K-R$150K implementation; R$10K-R$20K/mo retainer

### 2. HRTech/ATS Platform Product Manager
- **Profile**: Building or scaling recruitment platform for Brazilian mid-market, 100-500 client companies
- **Pain**: Keyword matching misses 40% of qualified candidates, clients complain about screening quality, losing deals to Gupy
- **Hook**: "Your ATS rejects candidates who write 'gestão de equipes' when the JD says 'liderança'. Our semantic matching catches what keywords miss"
- **Buying trigger**: A/B test showing matching accuracy improvement; client retention data correlated with screening quality
- **Budget**: R$100K-R$250K API integration; R$15K-R$30K/mo ongoing

### 3. EdTech/Bootcamp CEO
- **Profile**: Running coding bootcamp or professional training program, 200-2000 students/year
- **Pain**: Cannot prove employment outcomes to prospective students, no data on which skills actually land jobs, completion != employment readiness
- **Hook**: "Your competitors claim 90% employment rates but can't prove it. We connect your curriculum to actual job market data"
- **Buying trigger**: Dashboard showing skills gap between graduates and market requirements; competitor benchmarking
- **Budget**: R$80K-R$200K implementation; R$10K-R$25K/mo analytics retainer

### 4. Employment Agency (Agência de Emprego) Operations Manager
- **Profile**: Managing high-volume, lower-skill placements, 500-5000 candidates/month
- **Pain**: Manual screening at scale is impossible, high candidate churn, low placement rates, SINE integration is primitive
- **Hook**: "You process 2,000 candidates/month manually. Our pipeline auto-screens, matches, and ranks — your team just confirms the top matches"
- **Buying trigger**: Placement rate improvement projection; cost-per-placement reduction math
- **Budget**: R$60K-R$150K implementation; R$8K-R$15K/mo retainer

## Why Now — Urgency Signals (2025-2026)

- **HR tech market growing 15-20% YoY** with R$4B+ in Brazil — mid-market companies need AI to compete with well-funded leaders like Gupy
- **GenAI inflection point**: LLMs now handle Portuguese CV analysis at near-human quality — the technical barrier that blocked automation for years is gone
- **eSocial mandate fully enforced** — companies must submit structured employment data, creating rich datasets for ML models
- **LGPD enforcement maturing** — companies need compliant AI solutions, not ad-hoc tools; creates demand for properly architected systems
- **Remote work normalization post-COVID** expanded talent pools — makes automated matching more valuable as geographic constraints loosen
- **Bootcamp market saturating** — differentiation shifts from "we teach code" to "we guarantee employment outcomes," requiring data-driven proof
- **RAIS/CAGED data becoming more accessible** through Portal Emprega Brasil APIs — public employment data is now programmatically available
- **cv10x project provides production-tested components** — JP Ventures has working CV intelligence code ready to adapt for client engagements

## Related Portfolio Projects

- **cv10x**: CV optimization and career tools SaaS — provides reusable CV parsing, skills extraction, and matching components
- See `kb/projects/` for Education & HR related project implementations

## File Index

| File | Description | Last Updated |
|------|-------------|-------------|
| [market-context.md](market-context.md) | Market size, players, trends, data maturity | 2026-04-02 |
| [regulatory-map.md](regulatory-map.md) | CLT, eSocial, LGPD, MEC, SINE/MTE regulations | 2026-04-02 |
| [solution-patterns.md](solution-patterns.md) | 5 solution projects + reusable patterns | 2026-04-02 |
| [engagement-templates.md](engagement-templates.md) | Diagnostic + implementation playbooks | 2026-04-02 |
| [competitive-intel.md](competitive-intel.md) | Gupy, Kenoby, Revelo, ABLER, Bettha, Catho | 2026-04-02 |
| [case-studies.md](case-studies.md) | Projected engagement outcomes across 5 solution types | 2026-04-02 |
| [sales-playbook.md](sales-playbook.md) | Hooks, ICP, objection handling, pricing | 2026-04-02 |
| [tech-landscape.md](tech-landscape.md) | RAIS/CAGED, CBO, INEP, ATS APIs, recommended stack | 2026-04-02 |

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
