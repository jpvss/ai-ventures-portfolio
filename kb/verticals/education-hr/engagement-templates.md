---
title: "Education & HR — Engagement Templates"
type: engagement-templates
vertical: education-hr
language: en
last_compiled: 2026-04-02
sources: [raw/industry-templates.md]
freshness: quarterly
tags: [education-hr, engagement, diagnostic, implementation, playbook]
---

# Education & HR — Engagement Templates

## Engagement Arc Overview

All Education & HR engagements follow the standard JP Ventures arc: **Paid Diagnostic → Implementation → Retainer**. The diagnostic is always paid (never free), scoped at 2-3 weeks, and designed to deliver standalone value while naturally leading to implementation.

```
Week 0: Sales qualification (ICP fit, budget, timeline)
Weeks 1-3: Paid Diagnostic (R$25K-R$60K)
Weeks 4-16: Implementation Phase 1 (R$60K-R$250K)
Weeks 17+: Ongoing Retainer (R$10K-R$30K/mo)
```

## Diagnostic Template: AI Readiness Assessment for HR/EdTech

### Scope (2-3 Weeks)

**Week 1: Data & Process Audit**
- Map current recruitment/education workflow end-to-end (Miro/Figjam)
- Inventory all data sources: ATS database, CV repository, LMS data, eSocial feeds, job posting sources
- Assess data quality: completeness, consistency, format, volume, freshness
- Interview 3-5 key stakeholders: Head of Recruitment, CTO/Tech Lead, Operations Manager, end-users (recruiters/coaches)
- Document current KPIs and how they are measured (time-to-hire, placement rate, screening accuracy, cost-per-hire)

**Week 2: AI Opportunity Mapping**
- Identify top 5 automation/AI opportunities ranked by impact and feasibility
- Score each opportunity on: data readiness (1-5), technical feasibility (1-5), business impact (R$ value), time-to-value (weeks)
- Map current tech stack and integration points (ATS, HRIS, LMS, payroll, eSocial)
- Assess LGPD compliance posture for candidate data processing
- Benchmark against competitors (using competitive-intel.md framework)

**Week 3: Roadmap & ROI Presentation**
- Build 6-month AI implementation roadmap with 3 phases
- Calculate ROI for top 3 opportunities with conservative/optimistic scenarios
- Prepare executive presentation with findings, recommendations, and pricing
- Deliver diagnostic report (25-40 pages) with actionable recommendations
- Present to decision-makers with live demo of quick-win prototype (if applicable)

### Diagnostic Deliverables

| Deliverable | Format | Description |
|-------------|--------|-------------|
| Data Maturity Assessment | Scorecard (PDF) | 1-5 rating across 8 dimensions: volume, quality, structure, freshness, integration, governance, skills, infrastructure |
| Process Map | Miro board | End-to-end workflow with pain points, bottlenecks, and automation opportunities highlighted |
| AI Opportunity Matrix | Spreadsheet + visual | 5 opportunities scored on impact/feasibility with R$ estimates |
| Competitive Benchmark | Report section | Client positioning vs. 3-5 competitors on AI/data capabilities |
| LGPD Compliance Checklist | Checklist (PDF) | Gap analysis against LGPD requirements for AI-based candidate processing |
| Implementation Roadmap | Gantt + narrative | 6-month phased plan with milestones, dependencies, and team requirements |
| ROI Model | Spreadsheet | Conservative/optimistic projections for top 3 opportunities |
| Executive Presentation | Slide deck (20-30 slides) | Decision-ready summary for C-level/board presentation |

### Diagnostic Pricing

| Client Type | Diagnostic Price | Typical Duration |
|-------------|-----------------|-----------------|
| Outplacement consultancy (5-30 employees) | R$25K-R$35K | 2 weeks |
| Mid-market ATS platform (50-200 employees) | R$40K-R$60K | 3 weeks |
| Bootcamp/EdTech (30-150 employees) | R$30K-R$45K | 2-3 weeks |
| Employment agency (20-100 employees) | R$25K-R$35K | 2 weeks |

### Diagnostic-to-Implementation Conversion

**Target conversion rate**: 60-70% (diagnostic findings create urgency)

**Key conversion tactics**:
- Include a "quick win" prototype in the diagnostic (e.g., parse 100 CVs and show quality scores) — makes the opportunity tangible
- ROI model shows payback period < 6 months for Phase 1
- Roadmap Phase 1 is scoped to deliver value within 8-12 weeks
- Offer diagnostic fee credit toward Phase 1 implementation

## Implementation Template: CV Intelligence Platform

### Phase 1: Core Pipeline (Weeks 1-8, R$60K-R$90K)

**Deliverables**:
- CV parsing pipeline (PDF/DOCX → structured JSON)
- Skills extraction and CBO taxonomy mapping
- Quality scoring engine (ATS compatibility, completeness, impact language)
- Basic dashboard for consultants to review parsed CVs
- API for integration with client's existing tools

**Team**: 1 senior ML engineer (lead), 1 full-stack developer, 1 domain consultant (part-time)

**Milestones**:
- Week 2: CV parser handling 90%+ of Brazilian CV formats
- Week 4: Skills extraction with 85%+ accuracy on test set of 200 CVs
- Week 6: Quality scoring calibrated against senior consultant ratings
- Week 8: Dashboard + API deployed to staging; UAT with 3-5 consultants

### Phase 2: Optimization Engine (Weeks 9-14, R$40K-R$60K)

**Deliverables**:
- LLM-powered CV rewriting with style transfer
- ATS keyword optimization (match CV language to target JD requirements)
- Multi-format output generation (PDF, DOCX, LinkedIn text)
- Before/after comparison view
- Batch processing for high-volume clients

### Phase 3: Intelligence Layer (Weeks 15-20, R$30K-R$50K)

**Deliverables**:
- Market alignment scoring (CV skills vs. current job market demand from live postings)
- Career path recommendations based on skills graph
- Salary benchmarking integration (RAIS data)
- Analytics dashboard: trends, conversion rates, time savings

## Implementation Template: ATS Screening API

### Phase 1: Matching Engine (Weeks 1-10, R$100K-R$150K)

**Deliverables**:
- JD parsing and requirements extraction API
- CV parsing and structured profile API
- Semantic matching engine (embeddings + skills graph)
- Ranked candidate list with match scores and explanations
- REST API with OAuth2 authentication and rate limiting
- Bias audit pipeline (demographic parity testing)

**Team**: 1 senior ML engineer (lead), 1 backend developer, 1 NLP engineer, 1 domain consultant (part-time)

**Milestones**:
- Week 3: JD parser extracting requirements with 90%+ recall
- Week 5: Embedding-based matching prototype with 70%+ accuracy
- Week 7: Skills graph integration pushing accuracy to 80%+
- Week 9: Bias audit passing demographic parity thresholds
- Week 10: API deployed to staging; A/B test against client's current matching

### Phase 2: Advanced Features (Weeks 11-16, R$50K-R$80K)

**Deliverables**:
- Configurable scoring weights per client/JD type
- Candidate ranking with multiple criteria (fit, availability, salary expectation)
- Webhook callbacks for async processing
- Admin dashboard: matching quality metrics, bias monitoring, usage analytics
- Client SDK (Python, JavaScript)

### Phase 3: Continuous Learning (Weeks 17-22, R$30K-R$50K)

**Deliverables**:
- Feedback loop: recruiter accept/reject decisions retrain matching model
- A/B testing framework for scoring algorithm variants
- Automated model retraining pipeline (monthly)
- Performance degradation alerts

## Implementation Template: Employability Assessment Module

### Phase 1: Skills Mapping (Weeks 1-8, R$80K-R$120K)

**Deliverables**:
- Student skills inventory extraction (from projects, assessments, course completions)
- CBO + live market requirements aggregation
- Gap analysis engine (student vs. market requirements)
- Student-facing readiness dashboard
- Institution-facing cohort analytics dashboard

### Phase 2: Recommendations & Tracking (Weeks 9-14, R$40K-R$60K)

**Deliverables**:
- Personalized skill development recommendations
- Employment outcome tracking integration
- Employer-facing candidate validation portal
- Cohort comparison and trend analytics

## Retainer Template

### Standard Retainer Scope (R$10K-R$30K/mo)

| Service | Frequency | Included |
|---------|-----------|----------|
| Model monitoring & drift detection | Continuous | Automated alerts + monthly review |
| Model retraining | Monthly/Quarterly | Data refresh, accuracy recalibration |
| Bug fixes & minor enhancements | As needed | Up to 20 hours/month |
| Data source maintenance | Monthly | RAIS/CAGED/job posting scraper updates |
| LGPD compliance monitoring | Quarterly | Bias audit, consent compliance check |
| Performance reporting | Monthly | KPI dashboard review + recommendations |
| Strategic advisory | Monthly | 2-hour session on AI roadmap and priorities |
| Escalation support | As needed | 4-hour SLA for critical issues |

### Retainer Pricing Tiers

| Tier | Monthly Fee | Hours Included | Best For |
|------|------------|----------------|----------|
| Essentials | R$10K-R$15K | 15-20 hrs | Small outplacement firms, single solution |
| Growth | R$15K-R$22K | 25-35 hrs | Mid-market ATS, multiple integrations |
| Enterprise | R$22K-R$30K | 40-50 hrs | Large platforms, multiple solutions, SLA |

## Engagement Quality Gates

| Gate | Timing | Criteria | Action if Not Met |
|------|--------|----------|-------------------|
| Data quality check | Diagnostic Week 1 | Client has minimum viable data (100+ CVs, or 50+ JDs, or 6+ months of hiring data) | Scope down diagnostic; recommend data collection phase first |
| Stakeholder alignment | Diagnostic Week 2 | Decision-maker agrees on top 3 priorities | Facilitate alignment workshop before proceeding |
| Technical feasibility | Diagnostic Week 3 | At least 1 opportunity scores 4+ on feasibility | Adjust scope to achievable targets; avoid over-promising |
| Phase 1 acceptance | Implementation Week 8 | Core deliverables meet accuracy/performance thresholds | Extended testing period; scope adjustment for Phase 2 |
| Retainer value check | Month 3 of retainer | Client sees measurable improvement in target KPIs | Joint review and scope adjustment; escalate if needed |

---
*Compiled from: raw/industry-templates.md*
*Next review: 2026-07-02*
