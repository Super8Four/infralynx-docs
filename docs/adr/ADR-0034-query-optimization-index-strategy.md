# ADR-0034: Query Optimization And Index Strategy

## Status

Accepted

## Context

InfraLynx now exposes more CRUD, auth, RBAC, audit, backup, workflow, and caching surfaces, but the database layer is still abstract and cross-engine. Query and indexing strategy must be defined before persistent adapters arrive so API contracts and migration planning stay aligned.

## Decision

InfraLynx will:

- standardize offset-limit pagination at the API edge
- require deterministic sort order with a fallback column
- define index coverage from concrete query shapes
- ship engine-specific migration variants for PostgreSQL, MSSQL, and MariaDB
- validate query plans with engine-native explain tooling once persistent adapters land

## Consequences

### Positive

- query contracts stay stable before database persistence is finalized
- index intent is documented instead of implied
- cross-engine drift is reduced early

### Negative

- some optimization work is design-time until persistent adapters land
- shared indexes must stay conservative to avoid write regressions
