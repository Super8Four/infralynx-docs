# Search Filtering Logic

InfraLynx search applies filters after the result corpus is assembled and scored.

## Matching Rules

- query text is normalized to lowercase
- whitespace is collapsed before tokenization
- every query token must match somewhere in the record corpus
- title matches score higher than location, summary, or tag matches
- result ordering is stable by score, then domain, then title, then identifier

## Filter Rules

- `all` searches every supported domain
- domain filters narrow results to one domain without changing tokenization
- grouped results always preserve domain boundaries even when the filter is `all`

## Result Grouping

Results are grouped in fixed domain order:

1. Core Platform
2. IPAM
3. DCIM
4. Operations
5. Automation

This order is intentional and deterministic. It prevents relevance ties from producing inconsistent group ordering between runs.

## UI State Rules

- empty query keeps search idle
- non-empty query triggers centralized fetch
- failed requests produce a retryable error state
- selected results remain explicit by result ID

## Future Extension

Later indexing engines may improve ranking, but they must preserve:

- explicit domain grouping
- domain filter semantics
- deterministic tie-breaking
