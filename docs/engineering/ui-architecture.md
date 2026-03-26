# UI Architecture

The InfraLynx frontend begins with a shell-first architecture:

- persistent navigation rail
- central workspace surface
- contextual right-side rail

This keeps domain applications modular while preserving a consistent product frame.

## Package Boundaries

- `apps/web` owns the browser runtime and route-level composition
- `@infralynx/ui` owns shell navigation, shared tokens, and reusable UI contracts
- domain packages continue to own business models rather than presentational concerns

## Shell Principles

- navigation is domain-led instead of feature-led
- the outer shell remains stable while domain workspaces evolve independently
- shared tokens and navigation structure live outside the app runtime to reduce drift
- the first working surface should feel operational, not marketing-led

## Current Interaction Model

- hash-driven navigation for immediate browser-native section switching
- active navigation state mirrored in the workspace header
- shared shell panels that summarize cross-domain platform status

## Deferred Work

Later chunks should add:

- route-aware domain workspaces
- data loading and selection state
- command surface and search
- contextual inspectors and entity detail views
