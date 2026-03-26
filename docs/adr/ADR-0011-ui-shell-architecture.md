# ADR-0011: UI Shell Architecture

- Title: UI Shell Architecture
- Status: Accepted

## Context

InfraLynx needs a frontend shell before cross-domain workflows can be integrated. Without a stable shell, domain UIs would emerge as isolated screens with inconsistent navigation, layout, and visual language.

## Decision

InfraLynx will:

- establish `apps/web` as a real browser app runtime
- introduce `@infralynx/ui` for shared shell navigation, tokens, and UI contracts
- use a shell-first layout with left navigation, central workspace, and right context rail
- keep navigation domain-led and keep the shell visually aligned with the InfraLynx dark operational design language

## Consequences

- future domain surfaces can be added inside a stable product frame
- shared navigation and shell behavior remain reusable instead of being redefined per feature
- frontend implementation now has a clear separation between UI system concerns and domain concerns
- richer routing, data loading, and inspectors remain future work rather than being improvised in this chunk
