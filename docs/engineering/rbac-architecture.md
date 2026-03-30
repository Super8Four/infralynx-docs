# RBAC Architecture

InfraLynx now treats authorization as a first-class platform service rather than a thin role-name check.

## Core Layers

- `@infralynx/core-domain` owns permissions, roles, scoped assignments, provider mappings, and evaluation helpers.
- `@infralynx/auth-core` persists role assignments and provider-role mappings next to providers, users, and sessions.
- `apps/api/src/rbac` exposes the administrative RBAC surface and shared request-enforcement helpers.
- `apps/web/src/pages/admin/rbac` provides the operator UI for role assignments and provider-role mappings.

## Enforcement Model

- API enforcement is authoritative.
- UI enforcement is advisory and experience-oriented.
- Request handlers ask for permission IDs plus optional scope context.
- Identity providers can map groups or claims into scoped role assignments.

## Scope Types

- `global`: unrestricted administrative scope
- `tenant`: tenant boundary
- `site`: physical site boundary
- `device`: object-level device boundary

## Design Rules

- permissions stay stable and machine-readable
- routes and UI actions consume permission summaries, not raw role-name logic
- external identity mapping is normalized before authorization evaluation
- domains reference RBAC by IDs and scopes, never embedded provider-specific objects
