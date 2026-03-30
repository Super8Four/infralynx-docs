# Audit Query Patterns

The audit API is optimized for operational filters rather than free-form search.

## Primary Filters

- `userId`
- `action`
- `objectType`
- `objectId`
- `tenantId`
- `since`
- `until`
- `limit`

## Common Queries

- recent changes for one tenant
- all changes to a device or prefix
- provider configuration changes
- failed job and webhook activity
- RBAC assignment history

## Operational Guidance

- use narrow filters for incident review
- prefer time windows for large datasets
- keep audit reads separate from the global search surface
