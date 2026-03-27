# Scheduler API

The scheduler API manages recurring trigger definitions.

## Endpoints

- `GET /api/schedules`
- `POST /api/schedules`
- `GET /api/schedules/{id}`
- `PUT /api/schedules/{id}`
- `DELETE /api/schedules/{id}`
- `GET /api/schedules/logs`

## Required Headers

- `X-InfraLynx-Actor-Id`
- `X-InfraLynx-Role-Ids`
- `X-InfraLynx-Tenant-Id` optional, defaults to platform

## Example Create Payload

```json
{
  "name": "Daily topology refresh",
  "cronExpression": "0 6 * * *",
  "timezone": "UTC",
  "jobType": "core.echo",
  "payload": {
    "message": "scheduled refresh"
  },
  "enabled": true
}
```

## Access Model

- `schedule:read` for viewing schedules and logs
- `schedule:write` for create, update, and delete
