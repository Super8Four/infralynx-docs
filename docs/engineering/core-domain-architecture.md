# Core Domain Architecture

The core platform layer defines the shared business contracts that other InfraLynx domains depend on before DCIM, IPAM, or automation-specific models are introduced.

## Scope

The initial core-domain skeleton covers:

- tenants
- tagging
- statuses
- permissions
- roles
- media linking support

These contracts stay intentionally small so later domains can depend on stable identifiers and service boundaries without inheriting application-specific logic too early.

## Package Boundaries

- `@infralynx/core-domain` owns base entities and RBAC-oriented contracts
- `@infralynx/auth` owns identity, session, and authorization decision scaffolds
- `@infralynx/audit` owns append-only audit event contracts and summaries
- `@infralynx/media-core` owns media metadata, linking, validation, and access-control helpers

## Design Rules

- core entities must remain persistence-agnostic
- authorization contracts belong to shared core packages, not app runtimes
- package boundaries should reflect ownership, not convenience reuse
- audit recording is append-only by design and should not become a mutable activity log

## Early Service Scaffolds

The current skeleton provides:

- tenant directory indexing
- role indexing
- access-decision evaluation from role assignments
- audit record construction and summarization

These are baseline service helpers only, not final runtime implementations.
