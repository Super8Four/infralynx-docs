# Audit API

## Endpoints

- `GET /api/audit`
- `GET /api/audit/{id}`

## Query Parameters

- `userId`
- `action`
- `objectType`
- `objectId`
- `tenantId`
- `since`
- `until`
- `limit`

## Notes

- audit reads require `audit:read`
- records are append-only
- query results are returned newest first
