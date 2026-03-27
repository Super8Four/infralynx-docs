# Webhook Delivery Guarantees

InfraLynx uses the background job engine to deliver webhooks asynchronously.

## Delivery model

- Event emission stores the event record first.
- Matching webhooks create `webhook.deliver` jobs.
- Worker processes lease delivery jobs from the shared queue.
- Successful deliveries are recorded with response status and timestamp.

## Retry behavior

- Delivery retries use the shared job retry policy.
- A failed attempt returns the job to `pending` until retries are exhausted.
- Delivery attempts are recorded separately from job logs.
- Permanent failure leaves the job in `failed`.

## Current guarantee level

- At-least-once delivery within the bounds of the bootstrap queue implementation.
- Ordering is best effort and follows queue order, not a global sequencing contract.
- Duplicate-safe consumers are required because retries can re-deliver the same event.

## Future work

- configurable backoff
- dead-letter handling
- alerting and escalation
- higher-scale queue backends
