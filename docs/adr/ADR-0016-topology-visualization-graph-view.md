# ADR-0016: Topology Visualization Graph View

## Title

Topology Visualization Graph View

## Status

Accepted

## Context

InfraLynx needs a first interactive network topology view that shows device relationships without introducing an overbuilt graph engine early in the platform lifecycle.

The system already has:

- explicit device and cable records
- deterministic topology and path-tracing helpers
- a UI shell with API-backed data integration

The missing layer is a graph view that translates those records into an operator-facing network map while preserving domain boundaries.

## Decision

InfraLynx will implement topology visualization with three layers:

1. `packages/network-domain/src/topology-view` for deterministic node and edge generation
2. `packages/ui/src/topology` for reusable filter and graph-view helpers
3. `apps/web/src/components/topology` for SVG rendering and interaction behavior

The initial graph view will:

- render device nodes
- render explicit connection edges
- support filtering by site, role, and VLAN
- support zoom, pan, and node selection

Layout will remain simple and deterministic rather than adopting a more complex graph engine at this stage.

## Consequences

Positive:

- the graph model is testable without browser dependencies
- the UI remains decoupled from raw backend domain payloads
- operator behavior is stable across refreshes

Negative:

- layout quality will be basic compared with a full graph engine
- large topologies may eventually need virtualization or clustering
- richer edge routing and graph editing are deferred
