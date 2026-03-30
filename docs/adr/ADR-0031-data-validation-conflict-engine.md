# ADR-0031: Data Validation Conflict Engine

## Status

Accepted

## Context

InfraLynx already had resource-local validation for inventory payloads, but that was not enough to prevent cross-record integrity problems such as overlapping prefixes, duplicate IPs, or broken device/interface references.

The platform also needed a dry-run validation path for approval-driven changes.

## Decision

InfraLynx will use a centralized validation package that evaluates the candidate post-mutation inventory snapshot.

Key decisions:

- validation runs before writes
- conflict detection is separate from field validation
- dry-run validation reuses the same mutation planning path as committed writes
- approval workflows can require validation before a change-control request is created

## Consequences

Positive:

- invalid cross-domain state is blocked before persistence
- dry-run and committed write behavior stay aligned
- approval-driven change requests can fail early with structured conflict output

Tradeoffs:

- write operations now pay a validation cost before persistence
- the bootstrap engine is still conservative for IPv6 conflict analysis
