# ADR-0036: API Versioning and Contract Hardening

## Status

Accepted

## Context

InfraLynx had accumulated a growing API surface without a stable namespace, centralized schema validation, or a consistent versioned error model. That was acceptable during early scaffolding but not for long-term integrations.

## Decision

InfraLynx will:

- treat `/api/v1` as the stable integration namespace
- validate versioned requests centrally with Zod
- normalize versioned JSON responses to include shared metadata
- preserve legacy `/api/*` routes temporarily with explicit deprecation signaling

## Consequences

Positive:

- external integrations get a stable namespace
- request validation is consistent across the primary API surface
- deprecation becomes explicit rather than implicit

Tradeoffs:

- legacy and versioned routes must coexist for a migration window
- response normalization adds a small amount of API-layer indirection
