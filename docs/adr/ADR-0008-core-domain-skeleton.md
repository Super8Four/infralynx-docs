# ADR-0008: Core Domain Skeleton

- Title: Core Domain Skeleton
- Status: Accepted

## Context

InfraLynx needs a stable platform-level core before domain modules such as IPAM and DCIM can be introduced. Authentication, RBAC, tenants, tagging, statuses, and audit logging are foundational capabilities, but implementing full runtime services too early would create avoidable coupling.

## Decision

InfraLynx will introduce three focused packages:

- `@infralynx/core-domain`
- `@infralynx/auth`
- `@infralynx/audit`

These packages will define typed entities, baseline service helpers, and package boundaries without introducing persistence, provider integrations, or transport-specific behavior.

## Consequences

- future domains can depend on stable core contracts early
- authentication and authorization remain modular instead of leaking into app runtimes
- audit logging starts as an append-only contract, not an implementation-specific log store
- richer identity, policy, and tenant workflows are deferred to later chunks
