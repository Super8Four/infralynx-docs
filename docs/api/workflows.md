# Workflows API

The workflows API manages approval requests and approval decisions.

## Endpoints

### `GET /api/workflows`

Returns the visible approval requests and aggregate status counts for the current reviewer context.

### `POST /api/workflows`

Creates a new approval request.

Expected fields:

- `type`
- `title`
- `payload`
- `assignedUserIds`
- `assignedRoleIds`

Optional fields:

- `tenantId`
- `siteId`
- `deviceId`
- `jobType`
- `jobPayload`

### `GET /api/workflows/{id}`

Returns one approval request by ID.

### `POST /api/workflows/{id}/approve`

Approves a pending request. If the request has an execution binding, approval enqueues the linked job through the standard job engine.

### `POST /api/workflows/{id}/reject`

Rejects a pending request.

## Permission Requirements

- `workflow:read`
- `workflow:write`
- `workflow:approve`

## Notes

- approvals are role-aware and tenant-aware
- execution is indirect through jobs
- requests are auditable through the shared audit trail
