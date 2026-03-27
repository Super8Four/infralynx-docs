# Search Query Patterns

InfraLynx search is currently optimized for operational lookup patterns rather than natural-language search.

## Supported Query Shapes

- exact identifiers
  - `tenant:read`
  - `vlan-120`
- partial names
  - `leaf`
  - `compute`
- CIDR and IP fragments
  - `10.40`
  - `172.20.10`
- role or function terms
  - `spine`
  - `top-of-rack`
  - `power`
- site and location terms
  - `Dallas`
  - `Phoenix`

## Query Guidance

- broad operational keywords are useful for exploration
- more specific terms narrow quickly because all tokens must match
- domain filters are the correct way to narrow by area instead of overloading the query string

## Response Contract

The search API returns:

- normalized query text
- selected domain filter
- result counts by domain
- grouped results with match terms
- guidance for UI behavior

## Non-Goals in This Phase

- fuzzy typo tolerance
- semantic intent expansion
- weighted business relevance
- direct database search from the frontend
