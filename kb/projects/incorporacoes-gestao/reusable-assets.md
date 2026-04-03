---
title: "Incorporacoes Gestao — Reusable Assets"
type: project
slug: incorporacoes-gestao
language: en
last_compiled: 2026-04-02
---

# Incorporacoes Gestao — Reusable Assets

## Technical Components

- **Precision financial apportionment engine:** Decimal.js-based proportional distribution by ideal fraction with remainder allocation, barter exclusion, and 100% sum validation. Reusable for any financial splitting system (condominiums, partnerships, revenue share).
- **Three-layer access control system:** Middleware + Server Action + query scope isolation. Pattern for any multi-tenant application with sensitive financial data.
- **DWG/DXF processing pipeline:** QCAD conversion -> Python metadata extraction -> image rendering. Reusable for construction, engineering, and architecture products.
- **3D model viewer component:** Three.js/R3F with GLB loading and orbital camera controls. Reusable for any product requiring 3D visualization.
- **Auditable financial PDF generator:** @react-pdf/renderer with category breakdown, investor-specific data, and audit trail. Reusable for any investor reporting or accountability tool.
- **Role-based investor portal:** Read-only portal with data isolation for external stakeholders. Reusable for any product serving multiple investor/client groups.
- **Prisma + NextAuth multi-tenant pattern:** Type-safe ORM with role-based authentication and query scoping. Reusable architecture for SaaS with multiple user roles.

## Patterns That Map to kb/patterns/

- Auditable financial reporting (cross-reference: `kb/patterns/auditable-reporting.md`)
- Regulatory modeling / Lei 4.591/64 (cross-reference: `kb/patterns/regulatory-modeling.md`)
- Multi-tenant access control (cross-reference: `kb/patterns/multi-tenant-access.md`)
- Financial ETL and reconciliation (cross-reference: `kb/patterns/financial-etl.md`)

## Data Sources and Integrations

- **CUB/Sinduscon:** Construction cost reference by state and standard — for budget reviews
- **INCC/FGV:** Construction cost index for contractual adjustments
- **Cartorio de RI:** Development registration with memorial, convention, and ideal fractions
- **Prefeituras:** Construction permits, habite-se, and urbanistic parameters
- **QCAD:** Open-source CAD tool for DWG/DXF conversion
- **Supabase Storage:** File management for architectural documents and 3D models
