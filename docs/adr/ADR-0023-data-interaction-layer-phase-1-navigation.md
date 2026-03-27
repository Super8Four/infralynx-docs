# ADR-0023: Data Interaction Layer and Phase 1 Navigation

## Status

Accepted

## Context

InfraLynx had a strong shell, visualization surfaces, and API integration patterns, but it did not yet provide consistent operator CRUD workflows across core DCIM and IPAM resources. Navigation also still reflected broader domain intent rather than only the features that were actually usable in the application.

## Decision

InfraLynx will add a Phase 1 data interaction layer with these rules:

- CRUD pages are API-driven
- writable resources use a shared page pattern
- read-only resources use the same list/detail interaction model where full CRUD is not yet required
- navigation exposes only implemented and usable resources
- relationship display is mandatory on resource detail pages

Phase 1 writable resources are:

- sites
- racks
- devices
- prefixes
- IP addresses

## Consequences

- The platform becomes usable as an operator workspace instead of a shell-only demo.
- The API now owns explicit inventory contracts and related-object payloads.
- Navigation becomes narrower and clearer, but some future domains remain intentionally hidden.
- The file-backed inventory persistence model remains a temporary adapter that will later need replacement by database-backed storage.
