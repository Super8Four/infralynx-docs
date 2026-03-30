# ADR-0028: Advanced RBAC (Scoped + Provider-Aware)

## Status

Accepted

## Context

InfraLynx originally used coarse role-based permission checks. That was not sufficient for tenant, site, and device boundaries or for external provider-driven role mapping.

## Decision

InfraLynx will use:

- permission IDs in `resource:action` form
- scoped role assignments
- provider-role mappings for LDAP, OIDC, and SAML inputs
- API-first authorization enforcement with UI permission summaries

## Consequences

- authorization decisions become more explicit and reusable
- external providers can be integrated without leaking provider logic across the platform
- RBAC administration now needs a dedicated API and UI surface
