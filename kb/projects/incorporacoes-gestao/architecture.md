---
title: "Incorporacoes Gestao — Architecture"
type: project
slug: incorporacoes-gestao
language: en
last_compiled: 2026-04-02
---

# Incorporacoes Gestao — Technical Architecture

## Tech Stack Choices and Rationale

- **Next.js 16 + React 19:** Full-stack framework with Server Actions for financial operations and Server Components for dashboard rendering. Middleware for authentication and role-based access control.
- **Prisma 6 + PostgreSQL:** Type-safe ORM with migrations for structured financial data. PostgreSQL for ACID transactions critical to financial operations.
- **NextAuth v5:** Authentication with role-based access (ADMIN/INVESTOR). Integrates with middleware for route protection.
- **Decimal.js:** Precision arithmetic library for financial calculations — avoids JavaScript floating-point errors in apportionment calculations where cent-level accuracy is legally required.
- **@react-pdf/renderer:** React-based PDF generation for monthly investor reports — allows component-level PDF authoring with the same patterns as UI development.
- **Three.js / @react-three/fiber / @react-three/drei:** Browser-based 3D visualization for architectural models (GLB files) with orbital camera controls.
- **Supabase Storage:** File storage for uploaded DWG/DXF files and generated floor plan images.
- **Python:** DWG/DXF processing pipeline — conversion via QCAD, metadata extraction, floor plan image generation.

## Data Architecture

- **Database:** PostgreSQL via Prisma — projects, units, investors, expenses, payments, apportionments, audit logs
- **Financial model:** Decimal(15,2) precision throughout — ideal fractions, expense amounts, apportionments
- **File storage:** Supabase Storage for DWG/DXF files, floor plan images, and 3D models (GLB)
- **Access control:** Three-layer isolation — middleware (route), Server Actions (operation), query scoping (data)

## Key Technical Patterns

- **Precision financial apportionment:** Decimal arithmetic for proportional distribution by ideal fraction with remainder allocation and 100% sum validation. Critical for legal compliance.
- **Three-layer access control:** Middleware -> Server Action -> query scope. Ensures no data leakage between investors at any level.
- **DWG/DXF processing pipeline:** External tool (QCAD) conversion -> Python extraction -> image rendering. Pattern for technical document processing.
- **Role-based multi-tenant architecture:** ADMIN sees all, INVESTOR sees only own data. Implemented via Prisma query scoping based on session user.
- **Audit trail pattern:** Every financial operation logged with timestamp, user, previous/new values. Required for legal accountability.
- **3D model viewer:** GLB loading with Three.js/R3F for architectural visualization. Pattern for construction/engineering products.

<!-- TO BE ENRICHED: Add learnings from project development -->

## Performance Considerations

- Prisma query scoping ensures investors only load their own data — reduces query size and enforces isolation
- PDF generation is server-side and can be CPU-intensive for large reports — consider background generation for multiple plants
- Three.js GLB models need optimization for browser loading — LOD and compression important

<!-- TO BE ENRICHED: Add learnings from project development -->

## Deployment Architecture

- Vercel hosting with Server Actions and API routes
- PostgreSQL database (managed)
- Supabase Storage for file management
- Python pipeline runs separately for DWG/DXF processing

<!-- TO BE ENRICHED: Add learnings from project development -->
