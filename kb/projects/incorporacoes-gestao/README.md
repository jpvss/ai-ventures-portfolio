---
title: "Incorporacoes Gestao"
type: project
slug: incorporacoes-gestao
vertical: investment-advisory
language: en
last_compiled: 2026-04-02
---

# Incorporacoes Gestao

**Type:** SaaS / Real estate financial management tool

**Description:** Financial and operational management system for real estate developments under administration (condominial construction).

## Problem It Solves

Investor groups in condominial real estate developments (Lei 4.591/64) depend on manual spreadsheets to track expenses, calculate proportional apportionments by ideal fraction per unit, and provide monthly accountability. Cent-level errors in apportionment generate conflicts between investors, and lack of transparency about construction progress and payments erodes group trust.

## Key Features

- Financial apportionment engine with Decimal(15,2) precision, normalization by ideal fraction, remainder distribution to largest investor, and 100% sum validation
- Complete project management with units, investors, investment status (ACTIVE/DEFAULTING/SUSPENDED), and barter unit handling
- Read-only investor portal with data isolation (Investor A never sees Investor B's data), interactive floor plans, and construction progress tracking
- DWG/DXF file processing pipeline: QCAD conversion, Python data extraction, per-floor plan rendering with zoom/pan visualization
- Monthly PDF report generation with expense breakdown by category, apportionment summary, amounts due/paid per investor, and audit trail

## Tech Stack

| Technology | Role |
|---|---|
| Next.js 16 | Full-stack framework |
| React 19 | UI rendering |
| TypeScript | Type safety |
| Tailwind CSS v4 | Styling |
| shadcn/ui | Component library |
| Prisma 6 | ORM |
| PostgreSQL | Database |
| NextAuth v5 | Authentication |
| Zod 4 | Validation |
| Recharts | Data visualization |
| @react-pdf/renderer | PDF generation |
| Three.js | 3D visualization |
| @react-three/fiber | React Three.js integration |
| @react-three/drei | Three.js helpers |
| Supabase Storage | File storage |
| Decimal.js | Precision arithmetic |
| Python | DWG/DXF processing |
| Vercel | Deployment |

## Capabilities Demonstrated

- Regulatory financial modeling with decimal precision for proportional apportionment per Lei 4.591/64, including ideal fraction normalization, barter exclusion, and rounding remainder distribution
- Multi-tenant system with role-based access control (ADMIN/INVESTOR) in three layers — middleware, Server Actions, and query scoping — ensuring total financial data isolation between investors
- Technical engineering document processing pipeline: DWG->DXF conversion, automated architectural metadata extraction (zoning, areas, floors), and interactive floor plan rendering
- Browser-based 3D architectural model visualization with Three.js/React Three Fiber, including GLB loading and orbital camera controls
- Auditable financial PDF document generation with category breakdown, amounts due/paid per investor, and persistent audit log for compliance

## Target Opportunities

| Segment | Project Type | Price Range | MVP Timeline |
|---|---|---|---|
| Real Estate / Condominial developers & SPEs | Management and accountability platform for construction condominiums and real estate SPEs | R$ 35k-60k | 3-4 weeks |
| Construction / Mid-size builders | Cost control and physical-financial progress dashboard for construction projects | R$ 30k-55k | 3-4 weeks |
| Property Management / Condo administrators | Intelligent apportionment and accountability system for residential and commercial condominiums | R$ 20k-40k | 2-3 weeks |
| Legal / Real estate law firms | Financial audit tool for condominial and development litigation | R$ 30k-55k | 3-4 weeks |

## Vertical Relevance

**Primary:** investment-advisory (investor reporting, financial accountability for real estate asset portfolios)

Also relevant to: adjacent (construction management, property management, legal audit tools)

## Links

- **Deploy:** https://incorporacao-do-digao.vercel.app
- **Repository:** Private
