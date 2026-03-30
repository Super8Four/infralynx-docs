# Query Standards

InfraLynx standardizes read patterns before persistent database adapters land. The current API uses file-backed stores, but query contracts already follow the shapes that the database layer will need.

## Standards

- normalize pagination at the API edge
- keep sorting deterministic with a fallback column such as `id`
- filter before pagination
- avoid repeated per-row relationship expansion when the same related dataset can be indexed once
- keep query semantics engine-neutral unless a capability note explicitly says otherwise

## Pagination Contract

- `page` starts at `1`
- `pageSize` defaults to `25`
- `pageSize` is capped at `100`
- responses must return pagination metadata so UI behavior stays predictable across engines

## Search And Listing

- search and list endpoints must accept normalized query text
- query-time enrichment should stay bounded and cache-friendly
- list responses should not rely on nondeterministic ordering
