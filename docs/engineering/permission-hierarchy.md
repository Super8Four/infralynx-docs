# Permission Hierarchy

InfraLynx permissions follow `resource:action`.

## Resources

- core: `tenant`, `user`, `role`, `permission`, `auth-provider`, `session`, `rbac`
- operations: `job`, `transfer`, `event`, `webhook`, `schedule`, `media`
- inventory: `site`, `rack`, `device`, `prefix`, `ip-address`, `vrf`, `interface`, `connection`

## Actions

- `read`
- `write`
- `delete`
- `execute`
- `assign`

## Hierarchy Rules

- role evaluation grants permissions
- scoped assignments narrow where a granted permission is valid
- the API must evaluate scope before mutation or sensitive reads
- the UI can hide actions when the permission is absent, but that is not the source of truth

## Default Roles

- `core-platform-admin`: global administrative control
- `core-tenant-operator`: tenant-scoped operational access
- `core-auditor`: read-only access
