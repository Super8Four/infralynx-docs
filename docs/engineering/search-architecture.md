# Search Architecture

InfraLynx search is a centralized API-driven service layer, not a UI-side aggregation pattern.

## Search Flow

1. The web shell sends a single request to `/api/search`.
2. The API assembles explicit records from core, IPAM, DCIM, and operations reference data.
3. `@infralynx/core-domain` applies tokenization, partial-match scoring, and result grouping.
4. The web application normalizes the response and renders grouped results.

## Ownership

- `packages/core-domain/src/search` owns query normalization, keyword matching, ranking, and grouping contracts.
- `apps/api` owns record assembly and the search endpoint.
- `apps/web/src/services/search` owns transport and normalization into UI models.
- `apps/web/src/hooks` owns request lifecycle and retry behavior.
- `apps/web/src/state` owns reducer-backed query, filter, and selection state.
- `apps/web/src/components/search` owns rendering and interaction.

## Architectural Constraints

- UI components must not query domain endpoints directly for search.
- Search relationships must remain explicit and record-based.
- Ranking must stay deterministic so later indexing systems can preserve user-visible behavior.
- Search filters must narrow the centralized result set, not rebuild results client-side from raw domain payloads.

## Future Direction

This baseline is designed so a future search index can replace only the API record source while preserving:

- the shared search query contract
- the response grouping model
- the UI data integration boundary
