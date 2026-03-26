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

## Database Compatibility Direction

InfraLynx must support:

- PostgreSQL
- Microsoft SQL Server
- MariaDB

Engineering documentation must make compatibility assumptions explicit and avoid undocumented vendor-specific behavior. The database abstraction layer, migration model, and CI matrix will each receive ADR-backed documentation as those chunks are implemented.

## ADR Relationship

Architecture decisions are not considered complete until they are recorded in the ADR section. Engineering documents should reference ADRs rather than restating decisions inconsistently across multiple pages.
