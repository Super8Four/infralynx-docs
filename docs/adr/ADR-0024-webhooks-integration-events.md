# ADR-0024: Webhooks and Integration Events

- Status: Accepted
- Date: 2026-03-27

## Context

InfraLynx needs a platform-level way to notify external systems when important changes occur. The notification model must not depend on UI behavior or inferred state. It also needs to reuse the existing job engine so outbound delivery does not block API mutations.

## Decision

InfraLynx will use an explicit event model backed by stored event records and webhook registrations.

- API write paths emit explicit events.
- Event records are persisted in `@infralynx/event-core`.
- Webhook registrations and delivery records are managed by `@infralynx/webhooks`.
- Matching deliveries are executed asynchronously through `webhook.deliver` jobs.
- Outbound requests are signed with HMAC SHA-256 using a per-webhook shared secret.

## Consequences

- Event ownership stays clear because only mutation handlers emit events.
- Delivery is asynchronous and retryable without adding a second worker system.
- Consumers must tolerate at-least-once delivery behavior.
- Advanced filtering, backoff policy, and secret-management hardening remain future work.
