# Event Model

InfraLynx emits explicit platform events when supported write operations occur. Events are not inferred from reads, polling, or UI behavior.

## Event record

Each event record contains:

- `id`
- `type`
- `payload`
- `created_at`

## Current event families

- `inventory.site.*`
- `inventory.rack.*`
- `inventory.device.*`
- `inventory.prefix.*`
- `inventory.ip-address.*`
- `job.created`
- `webhook.created`
- `webhook.updated`
- `webhook.deleted`

## Emission rules

- Events are created only by API write paths.
- Event payloads include the affected record or identifier.
- Event records are stored before delivery jobs are queued.
- Event types stay explicit so subscribers can filter deterministically.

## Ownership

- API mutation handlers decide when an event exists.
- `@infralynx/event-core` owns the durable event contract.
- `@infralynx/webhooks` consumes stored events for outbound delivery.
