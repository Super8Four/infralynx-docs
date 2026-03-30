# ADR-0029: Audit Logging (Structured + System-Wide)

## Status

Accepted

## Context

InfraLynx had local logging behavior inside individual services, but it did not yet have a centralized structured audit trail spanning authentication, inventory, jobs, webhooks, and RBAC administration.

## Decision

InfraLynx will use a centralized structured audit repository with:

- append-only records
- explicit object references
- JSON metadata
- API query access for authorized operators

## Consequences

- major system changes can be traced through one audit surface
- critical control-plane actions are no longer trapped inside subsystem-specific logs
- storage growth and query performance need dedicated follow-up work
