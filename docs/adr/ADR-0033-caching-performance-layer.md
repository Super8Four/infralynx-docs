# ADR-0033: Caching Performance Layer

## Status

Accepted

## Context

InfraLynx now has enough API-owned derived views, CRUD reads, RBAC summaries, and auth/session lookups that repeated uncached reads create avoidable recomputation and repository access.

## Decision

InfraLynx will use a centralized cache abstraction backed by Redis, with API-owned keys and explicit invalidation on successful writes.

## Consequences

- Redis details stay behind `@infralynx/cache-core`
- domain packages remain cache-agnostic
- auth, RBAC, inventory, and derived read responses gain bounded cache reuse
- invalidation complexity stays in API write handlers
- stale-data risk is reduced through short TTLs plus targeted invalidation
