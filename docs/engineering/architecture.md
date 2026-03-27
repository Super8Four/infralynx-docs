# Engineering Architecture

InfraLynx is being developed as a multi-repository program with explicit governance, documentation, infrastructure, design, and application boundaries.

## Engineering Documentation Framework

Engineering documentation must answer four questions clearly:

1. What problem is the subsystem solving?
2. What are the domain boundaries and dependencies?
3. What contracts, abstractions, and extension points exist?
4. What constraints must contributors preserve?

## Current Architectural Baseline

- `infralynx-platform` owns runtime code, services, frontend, and database integration.
- `infralynx-docs` owns ADRs, product docs, engineering docs, operations docs, API docs, and release notes.
- `infralynx-infra` owns deployment, environment, and infrastructure assets.
- `infralynx-standards` owns governance, templates, and collaboration policy.
- `infralynx-design` owns design system, flows, and visual standards.

## Platform Architecture Overview

The platform repository begins as a monorepo with explicit runtime separation:

- `apps/web`
- `apps/api`
- `apps/worker`

Shared packages are limited to configuration, core domain contracts, and low-coupling utilities so teams can scale without collapsing boundaries between runtimes.

The foundational platform packages now also include:

- `@infralynx/core-domain`
- `@infralynx/auth`
- `@infralynx/audit`
- `@infralynx/ipam-domain`
- `@infralynx/dcim-domain`
- `@infralynx/ui`
- `@infralynx/network-domain`
- `@infralynx/media-core`
- `@infralynx/media-storage`

The networking package is now split into two distinct concerns:

- cross-domain binding contracts
- deterministic topology and path-tracing helpers

The web application now adds a separate UI data integration layer:

- service functions for transport and normalization
- hook-based fetch orchestration
- reducer-backed UI state transitions

The UI layer now also includes a dedicated rack visualization system:

- shared rack geometry helpers in `@infralynx/ui`
- API-driven rack payloads
- interactive device and port selection in the web shell

The UI layer now also includes a topology visualization system:

- deterministic graph generation in `@infralynx/network-domain`
- reusable graph filtering helpers in `@infralynx/ui`
- interactive SVG rendering, zoom, pan, and selection in `apps/web`

The IPAM layer now also includes a dedicated hierarchy visualization system:

- hierarchy validation and utilization precomputation in `@infralynx/ipam-domain`
- reusable tree flattening helpers in `@infralynx/ui`
- expandable VRF and prefix rendering in `apps/web`

The UI layer now also includes a centralized search and filtering system:

- deterministic matching and grouping in `@infralynx/core-domain`
- centralized record assembly in `apps/api`
- transport, reducer state, and grouped-result rendering in `apps/web`

The UI layer now also includes a shared navigation system:

- route, breadcrumb, and context-link contracts in `@infralynx/ui`
- persistent shell layout and navigation rendering in `apps/web`
- explicit domain-to-route mapping for stable cross-domain movement

The core platform now also includes a standalone media service:

- metadata, link, and RBAC helpers in `@infralynx/media-core`
- local-first object storage adapters in `@infralynx/media-storage`
- upload and retrieval endpoints in `apps/api`

The core platform now also includes a standalone job engine:

- lifecycle and retry contracts in `@infralynx/job-core`
- queue persistence and job leasing in `@infralynx/job-queue`
- job creation and status endpoints in `apps/api`
- asynchronous execution in `apps/worker`

The core platform now also includes a standalone transfer service:

- format and schema validation in `@infralynx/data-transfer`
- import and export endpoints in `apps/api`
- job-engine-backed asynchronous import for larger payloads

## Database Compatibility Direction

InfraLynx must support:

- PostgreSQL
- Microsoft SQL Server
- MariaDB

Engineering documentation must make compatibility assumptions explicit and avoid undocumented vendor-specific behavior.

## Database Abstraction Baseline

The database layer is designed around three rules:

1. PostgreSQL is the reference engine for behavior and migration intent.
2. Compatibility must be expressed through explicit engine capabilities rather than assumption.
3. Migration versions stay aligned across engines even when SQL implementations differ.

Detailed guidance for the abstraction package, engine matrix, and migration rules is documented in the database abstraction design pages and ADRs.

## ADR Relationship

Architecture decisions are not considered complete until they are recorded in the ADR section. Engineering documents should reference ADRs rather than restating decisions inconsistently across multiple pages.
