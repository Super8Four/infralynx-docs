# Topology Visualization Architecture

InfraLynx topology visualization is split across three ownership layers so graph rendering does not leak into network modeling rules.

## Ownership Layers

- `packages/network-domain/src/topology-view` creates deterministic graph nodes and edges from explicit device and cable relationships.
- `packages/ui/src/topology` owns view-model filtering and selection helpers that are safe to reuse across frontend surfaces.
- `apps/web/src/components/topology` owns SVG rendering, viewport interaction, and operator-facing controls.

## Architectural Rules

1. Connections are explicit. The graph only renders relationships supplied by the backend contract.
2. Layout is deterministic. The same topology payload must produce the same node order and position.
3. Filtering is applied before rendering, not inferred during drawing.
4. UI state such as selection, zoom, and pan stays in the web layer.

## Runtime Flow

1. `apps/api` serves `/api/topology/demo`.
2. `apps/web/src/services/topology-graph.ts` normalizes the response.
3. `apps/web/src/state/topology-graph-state.ts` applies filter and viewport state.
4. `TopologyGraph.tsx` renders the filtered graph into an SVG canvas.

## Why This Split Exists

This keeps graph generation testable without a browser, keeps the UI package reusable, and avoids coupling the frontend directly to raw domain schemas.
