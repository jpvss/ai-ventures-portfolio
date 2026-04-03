---
title: "Incorporacoes Gestao — Learnings"
type: project
slug: incorporacoes-gestao
language: en
last_compiled: 2026-04-02
---

# Incorporacoes Gestao — Learnings

## What Worked Well

- **Decimal-precision apportionment engine** — Using Decimal.js with Decimal(15,2) precision for proportional expense allocation by ideal fraction, with normalization and remainder distribution to the largest investor, eliminated the cent-level rounding errors that caused real investor disputes in manual spreadsheet workflows.
- **Three-layer access control (middleware + Server Actions + query scoping)** — Implementing role-based isolation (ADMIN/INVESTOR) at three independent layers ensured that Investor A can never access Investor B's financial data, even if one layer is bypassed — a defense-in-depth approach required for financial data isolation.
- **DWG/DXF processing pipeline** — Converting architectural drawings from DWG to DXF via QCAD, extracting metadata (zoning, areas, floors) with Python, and rendering interactive per-floor plans with zoom/pan provided stakeholders with visual construction context alongside financial data.
- **Three.js 3D architectural visualization** — Browser-based 3D model rendering with GLB loading and orbital camera controls via React Three Fiber gave investors an immersive view of the development without requiring specialized architectural software.
- **Auditable PDF reports with category breakdown** — Generating monthly accountability PDFs with expense breakdown by category, amounts due/paid per investor, and persistent audit logs delivered investor-grade documentation that satisfies Lei 4.591/64 accountability requirements.

## Challenges Encountered

- **Lei 4.591/64 apportionment complexity** — Brazilian condominial construction law requires proportional expense allocation by ideal fraction, with special handling for barter units (permuta), defaulting investors, and suspended participation — edge cases that spreadsheet formulas routinely get wrong.
- **DWG file format variability** — Architectural DWG files from different CAD software (AutoCAD, SketchUp, ArchiCAD) produce inconsistent DXF conversions with varying layer naming conventions, requiring adaptive parsing rules for metadata extraction.
- **Investor data isolation in shared infrastructure** — Ensuring complete financial data isolation between investors sharing the same development required query-level scoping in every database access path — a single missed filter could expose another investor's payment status or outstanding balance.
- **Construction progress tracking granularity** — Mapping physical construction milestones to financial completion percentages requires domain expertise in construction scheduling; the system relies on admin input rather than automated progress detection, creating a manual bottleneck.

## Key Technical Decisions

- **Next.js 16 + Prisma 6 + PostgreSQL over spreadsheet automation** — Built a full web application rather than automating Excel because the multi-investor access control, audit trail, and regulatory calculation precision requirements exceed what spreadsheet-based solutions can reliably deliver.
- **NextAuth v5 for multi-role authentication** — Used NextAuth with role-based sessions (ADMIN vs. INVESTOR) to provide secure, per-user access without building a custom auth system, leveraging its credential provider for simple email/password login appropriate for a small investor group.
- **Prisma 6 ORM over raw SQL** — Chose Prisma for its type-safe query builder and migration system, ensuring that schema changes are tracked and reproducible — critical for a financial system where database structure changes must be auditable.
- **@react-pdf/renderer for client-side PDF generation** — Generated PDF reports on the client side rather than server side, keeping the Vercel deployment within serverless function limits while producing styled, multi-page financial documents with React components.

## Business Impact

- **Solved a real financial accountability pain point** — The system replaced a manual spreadsheet process that produced cent-level errors affecting real investor payments in a condominial construction project, demonstrating that financial precision tools have immediate, quantifiable value for investor groups.
- **Validated real estate development management as a market** — Condominial construction under Lei 4.591/64 is a growing segment in Brazil with no dominant software solution; the R$ 35k-60k engagement price point is accessible for SPEs (Sociedades de Proposito Especifico) managing R$ 5M-50M developments.
- **Demonstrated engineering document processing capability** — The DWG/DXF pipeline and Three.js 3D visualization prove the agency can handle technical engineering data, differentiating from pure data analytics consultancies — applicable to mining (mine plans), infrastructure (civil engineering), and construction.
- **Built reusable multi-tenant financial reporting** — The Prisma + NextAuth + role-based access pattern for investor-isolated financial reporting is directly portable to investment fund reporting, solar plant investor dashboards (Kiiry Dashboard successor), and insurance policy holder portals.
