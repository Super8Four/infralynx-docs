# ADR-0015 Rack Elevation Visualization

## Title

Rack Elevation Visualization

## Status

Accepted

## Context

InfraLynx needs a visual rack representation for DCIM workflows, but the platform is not ready for a full topology canvas or drag-and-drop editor. The first version must be accurate, reusable, and performant enough for standard cabinet views.

## Decision

InfraLynx will implement a grid-based rack elevation model.

The initial version will:

- use explicit U positions and device heights
- generate deterministic rack slots from shared helpers in `@infralynx/ui`
- render devices, ports, and a basic cable trace in the web application
- use click-based selection instead of drag-and-drop

## Consequences

Benefits:

- accurate U-position rendering
- reusable rack math outside the React layer
- lower complexity than a freeform canvas approach

Tradeoffs:

- cable rendering is basic rather than fully spatial
- no drag-and-drop placement yet
- very large racks and dense port sets may require later performance tuning
