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

The networking package is now split into two distinct concerns:

- cross-domain binding contracts
- deterministic topology and path-tracing helpers

The web application now adds a separate UI data integration layer:

- service functions for transport and normalization
- hook-based fetch orchestration
- reducer-backed UI state transitions

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
