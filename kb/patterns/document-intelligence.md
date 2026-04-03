---
title: Document Intelligence Pattern
type: pattern
language: en
last_compiled: 2026-04-02
sources:
  - kb/raw/industry-templates.md
freshness: current
tags:
  - document-intelligence
  - OCR
  - NLP
  - cross-vertical
verticals:
  - mining
  - insurance-surety
  - auctions
---

# Document Intelligence (OCR + NLP Pipelines)

Document-heavy workflows create bottlenecks in three of the four verticals. Mining, Insurance, and Auctions all process high volumes of unstructured or semi-structured documents that require extraction, validation, and transformation into actionable data. The same pipeline architecture applies across verticals with domain-specific extraction models.

## Vertical Implementations

| Vertical | Document Types | Volume Driver | Current Cost | AI-Enabled Cost |
|----------|---------------|---------------|-------------|-----------------|
| **Mining** | Environmental licenses (LP/LI/LO), condicionante documents, PRAD reports, dam safety declarations, NR-22 incident reports, RAL submissions | Multiple concurrent licenses with dozens of condicionantes each; monthly/quarterly monitoring reports | Manual tracking in Excel; environmental consulting fees | Automated extraction and deadline tracking |
| **Insurance/Surety Bonds** | Apolices, sinistro claims documents, edital documents for seguro garantia, financial statements (tomador analysis), court records | 44+ insurers processing thousands of policies; sinistralidade at 41.7% demands faster claims processing | Manual document review in underwriting; 5-day policy issuance | 30-minute issuance for standard risks; 67% faster claims resolution |
| **Auctions** | Editais (auction notices), matriculas (property registrations), certidoes (certificates), court filings | 275,000 transactions in 2024; 1,000+ leiloeiro sites; each property requires edital + matricula analysis | R$2,000/property for lawyer review | ~R$50/property with AI pipeline |

## Common Pipeline Architecture

```
[1. Ingestion]  →  [2. OCR]  →  [3. NLP Extraction]  →  [4. Validation]  →  [5. Structured Output]
```

### Stage 1: Document Ingestion
- PDF download from regulatory portals (ANM, SUSEP, TJ databases)
- Email attachment extraction
- Scanned document intake (physical documents digitized)
- Web scraping of document-heavy sites (leiloeiro websites, court portals)
- File format normalization (PDF, DOCX, images to standard processing format)

### Stage 2: OCR (Optical Character Recognition)

| Tool | Best For | Considerations |
|------|----------|---------------|
| **Azure AI Document Intelligence** | High-accuracy extraction from complex layouts; pre-built models for invoices, receipts, IDs | Recommended primary OCR; strong Portuguese support; pre-built and custom models; pay-per-page pricing |
| **Google Cloud Document AI** | Alternative to Azure; good Portuguese support | Comparable accuracy; choose based on client cloud posture |
| **Tesseract OCR** | Budget-conscious deployments; high-volume batch processing | Open-source; good for straightforward layouts; requires more tuning for complex documents |
| **Amazon Textract** | AWS-native deployments | Tables and forms extraction; integrates with AWS ecosystem |

**Recommendations**: Use Azure AI Document Intelligence as the primary OCR engine for complex documents (editais, matriculas, apolices) where layout matters. Use Tesseract for high-volume, simpler documents where cost optimization is critical. Always pre-process images (deskew, denoise, contrast enhancement) before OCR.

### Stage 3: NLP Extraction

After OCR produces raw text, NLP models extract structured information:

- **Named Entity Recognition (NER)**: Dates, monetary values, legal references, party names, property identifiers, regulatory codes
- **Relationship Extraction**: Link entities to their roles (tomador, segurado, leiloeiro, requerente)
- **Classification**: Document type, risk level, compliance status, claim category
- **Key-Value Extraction**: Structured fields from semi-structured documents (policy terms, edital conditions, license requirements)

**Tools and approaches**:
- **LLMs (GPT-4, Claude)**: Best for complex legal text interpretation, particularly Portuguese legal language in editais and regulatory documents. Use with structured prompts to extract specific fields.
- **spaCy with Portuguese models**: Good for NER and entity extraction at scale with lower per-document cost
- **Custom fine-tuned models**: When volume justifies the training investment (e.g., thousands of similar editais)
- **Rule-based extractors**: For highly structured documents with predictable formats (SUSEP reporting schemas, ANM submission forms)

### Stage 4: Validation

- Cross-reference extracted data against known databases (e.g., matricula numbers against cartorio records, CNPJ against Receita Federal)
- Confidence scoring: flag extractions below configurable threshold for human review
- Business rule validation (e.g., edital dates must be in the future, policy values must be positive, CFEM aliquots must match substance type)
- Duplicate detection across document corpus

### Stage 5: Structured Output

- Store extracted data in the unified data layer (see [data-integration.md](data-integration.md))
- Generate structured records: JSON/database rows with full provenance (source document, extraction confidence, validation status)
- Feed downstream systems: compliance engines, risk scorers, alert systems, search indices
- Maintain link back to source document for audit trail

## Vertical-Specific Extraction Models

### Mining: Environmental License Processing
- **Input**: LP/LI/LO license documents, condicionante lists, PRAD reports
- **Extract**: License type, validity dates, condicionante requirements, monitoring deadlines, responsible parties, geographic coordinates
- **Output**: Compliance calendar entries, monitoring task assignments, alert triggers
- **Value**: Prevents license suspension (operational halt costs R$500K-R$5M/day)

### Insurance: Policy and Claims Document Processing
- **Input**: Apolices, sinistro documentation, tomador financial statements, court records
- **Extract**: Policy terms, coverage amounts, claim details, financial ratios, judicial decisions
- **Output**: Underwriting risk inputs, claims triage decisions, fraud indicators
- **Value**: Policy issuance reduced from 5 days to 30 minutes; claims resolution from 45 to 15 days

### Auctions: Edital and Matricula Analysis
- **Input**: PDF editais from 1,000+ leiloeiro sites, matricula documents from cartorios, certidoes
- **Extract**: Property details (address, area, type), minimum bid, payment conditions, deadlines, encumbrances (onus, penhoras, hipotecas), pending lawsuits
- **Output**: Structured property records with risk scores, deadline alerts, investment scoring inputs
- **Value**: Legal analysis cost from R$2,000 to ~R$50/property; scales from 20 to 200+ analyses/month

## Implementation Considerations

### Portuguese Language Handling
- All documents are in Brazilian Portuguese with legal/regulatory terminology
- OCR models must handle Portuguese diacritics (a, e, o, c, etc.)
- NLP models need Portuguese legal vocabulary (e.g., "alienacao fiduciaria," "preco vil," "condicionante," "tomador")
- LLM-based extraction handles Portuguese natively; custom models require Portuguese training data

### Document Quality Variation
- Government-issued documents (licenses, certidoes) are generally well-structured but may be scanned copies
- Leiloeiro editais vary wildly in format across 1,000+ sites
- Older documents may have poor scan quality requiring pre-processing
- Build a quality classifier to route documents to appropriate processing paths

### Volume and Cost Optimization
- Tier documents by complexity: simple (rule-based extraction) vs. complex (LLM-based)
- Cache extraction results for documents that appear across multiple contexts
- Batch processing for non-time-critical documents; real-time for alerts and compliance deadlines
- Monitor per-document costs and optimize model selection accordingly

## Estimated Investment

| Vertical | Investment Range | Timeline | Expected Volume |
|----------|-----------------|----------|-----------------|
| **Mining** | R$200K-R$500K | 10-14 weeks | Hundreds of license documents, ongoing monitoring reports |
| **Insurance** | R$350K-R$700K | 5-7 months | Thousands of policies and claims documents per month |
| **Auctions** | R$200K-R$350K | 3-5 months | Hundreds to thousands of editais and matriculas per month |

## Cross-References

- Feeds into: [compliance-automation.md](compliance-automation.md) (extracted data validates compliance)
- Feeds into: [predictive-models.md](predictive-models.md) (extracted features for ML models)
- Feeds into: [alert-notification.md](alert-notification.md) (extracted deadlines trigger alerts)
- Depends on: [data-integration.md](data-integration.md) (output stored in unified data layer)
