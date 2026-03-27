# ADR-0014 UI Data Integration Layer

## Title

UI Data Integration Layer

## Status

Accepted

## Context

The InfraLynx UI shell needs live backend data, but directly binding React components to raw API payloads would create tight coupling and make error handling inconsistent.

## Decision

InfraLynx will use a separate UI data integration layer inside `apps/web` consisting of:

- services for transport and payload normalization
- hooks for asynchronous request orchestration
- reducer-backed state for explicit UI status transitions

The first integration target is `/api/overview`.

## Consequences

Benefits:

- frontend rendering stays decoupled from backend payload structure
- loading and error states are consistent
- future caching and mutation workflows have a clear extension point

Tradeoffs:

- more files than a direct fetch inside a component
- response normalization must be maintained deliberately as APIs evolve
