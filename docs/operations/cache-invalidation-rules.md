# Cache Invalidation Rules

InfraLynx invalidates cache entries from the same API surface that mutates the underlying state.

## Inventory

Invalidate after successful create, update, or delete of:

- sites
- racks
- devices
- prefixes
- IP addresses

Affected cache groups:

- inventory navigation
- inventory lists
- inventory details
- derived search and visualization responses

## Authentication

Invalidate after:

- login success
- session refresh
- logout
- provider create, update, or delete

Affected cache groups:

- enabled providers
- provider list and detail reads
- auth session status
- cached bearer identity resolution
- RBAC summaries that depend on auth state

## RBAC

Invalidate after:

- role assignment create or delete
- provider-role mapping create or delete

Affected cache groups:

- RBAC summary
- RBAC admin snapshot
- cached session identity and auth session reads

## Rules

- never invalidate on failed writes
- prefer targeted prefix invalidation over global flush
- keep invalidation in the write owner, not the consumer
