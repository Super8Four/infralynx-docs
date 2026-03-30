# Audit Model

InfraLynx uses a centralized structured audit log for critical system activity.

## Record Shape

- `id`
- `user_id`
- `actor_type`
- `tenant_id`
- `action`
- `object_type`
- `object_id`
- `metadata`
- `timestamp`

## Design Rules

- audit records are append-only
- object references are explicit
- metadata stays JSON and event-specific
- write-heavy paths should emit compact records instead of verbose payload mirrors

## Covered Activity

- authentication events
- CRUD mutations
- job creation and execution
- webhook configuration and delivery
- RBAC administration
