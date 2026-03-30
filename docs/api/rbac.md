# RBAC API

## Endpoints

- `GET /api/rbac`
- `GET /api/rbac/summary`
- `POST /api/rbac/assignments`
- `DELETE /api/rbac/assignments/{id}`
- `POST /api/rbac/provider-mappings`
- `DELETE /api/rbac/provider-mappings/{id}`

## Purpose

- inspect effective roles, permissions, assignments, and mappings
- manage user-role assignments
- manage provider-role mappings

## Notes

- RBAC management requires `rbac:read` or `rbac:write`
- scope-aware enforcement applies at API level
- UI clients should use the returned permission summary instead of duplicating policy rules
