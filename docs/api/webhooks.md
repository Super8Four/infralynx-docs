# Webhooks and Events API

## Endpoints

### `GET /api/webhooks`

Returns registered webhooks and supported event types.

### `POST /api/webhooks`

Registers a webhook.

Example payload:

```json
{
  "endpointUrl": "https://example.com/hooks/infralynx",
  "eventTypes": ["inventory.device.created", "job.created"],
  "enabled": true
}
```

### `GET /api/webhooks/{id}`

Returns the webhook record and recorded deliveries.

### `PUT /api/webhooks/{id}`

Updates endpoint URL, event filters, secret, or enabled state.

### `DELETE /api/webhooks/{id}`

Deletes the webhook registration.

### `GET /api/events`

Lists recorded events. Optional query:

- `type`

### `GET /api/events/{id}`

Returns an event and the delivery attempts associated with it.

## Authorization

Headers required:

- `X-InfraLynx-Actor-Id`
- `X-InfraLynx-Tenant-Id`
- `X-InfraLynx-Role-Ids`

## Permissions

- `event:read`
- `webhook:read`
- `webhook:write`
- `webhook:delete`
