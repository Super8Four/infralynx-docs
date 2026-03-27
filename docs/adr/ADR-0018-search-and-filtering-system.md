# ADR-0018: Search and Filtering System

- Title: Search and Filtering System
- Status: Accepted

## Context

InfraLynx now has multiple domain surfaces in the web shell, but no unified way to locate tenants, prefixes, devices, topology entities, or operational records across those domains.

Search must remain:

- centralized
- deterministic
- decoupled from raw frontend rendering
- compatible with a future indexing engine

## Decision

InfraLynx will implement search as a centralized API-driven service with shared matching and grouping logic in `@infralynx/core-domain`.

The system will:

- assemble explicit cross-domain search records in the API layer
- use deterministic tokenization, partial matching, scoring, and grouping in shared core-domain helpers
- expose grouped domain results through a single `/api/search` contract
- keep UI search state isolated in services, hooks, and reducer-backed state
- apply domain filters against the centralized result set rather than querying domain endpoints directly from the UI

## Consequences

Positive:

- search behavior is consistent across domains
- the UI remains decoupled from backend schema assembly details
- later search indexing can replace backend record sourcing without changing the UI contract

Negative:

- centralized search will need careful performance tuning as the corpus grows
- relevance is intentionally simple in the baseline and will need later refinement
- result freshness depends on backend record assembly rather than direct domain lookups
