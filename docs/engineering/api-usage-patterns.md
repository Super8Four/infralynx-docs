# API Usage Patterns

Chunk 13 introduces the first formal UI-to-API integration pattern for InfraLynx.

## Principles

- the UI consumes API payloads through dedicated service functions
- raw transport payloads are normalized before they reach React components
- domain IDs stay explicit and stable across layers
- rendering code does not shape API requests directly

## Current Flow

1. The web app requests `/api/overview`.
2. `src/services/api-client.ts` handles transport and HTTP failures.
3. `src/services/domain-overview.ts` normalizes the payload into UI-specific contracts.
4. React hooks and reducer-backed state deliver a render-safe model to the shell.

## Contract Discipline

- backend payloads may evolve as long as the UI normalization layer is updated deliberately
- React components should consume normalized models, not backend response types spread across the app
- future mutation calls should follow the same transport-and-normalization boundary
