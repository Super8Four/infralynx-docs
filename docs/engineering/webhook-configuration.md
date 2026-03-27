# Webhook Configuration

Webhooks provide outbound notifications for explicit InfraLynx events.

## Webhook record

Each webhook stores:

- `id`
- `endpoint_url`
- `event_types`
- `secret`
- `enabled`
- `created_at`
- `updated_at`

## Configuration rules

- Endpoint URLs must use `http` or `https`.
- A webhook must subscribe to at least one event type.
- Event filters are exact event names, with optional `*` for all supported events.
- Disabled webhooks stay registered but do not receive delivery jobs.

## Registration flow

1. Client calls `POST /api/webhooks`.
2. InfraLynx validates the endpoint and filter set.
3. The webhook is stored.
4. A `webhook.created` event is emitted.
5. Matching delivery jobs are queued through the job engine.

## Update and delete

- `PUT /api/webhooks/{id}` updates endpoint URL, filters, secret, or enabled state.
- `DELETE /api/webhooks/{id}` removes the registration and emits `webhook.deleted`.
