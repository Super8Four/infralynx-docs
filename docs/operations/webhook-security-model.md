# Webhook Security Model

Webhook security is intentionally simple in the bootstrap phase, but the core controls are explicit.

## Current controls

- webhook registration requires RBAC
- event reading requires RBAC
- delivery uses per-webhook shared secrets
- every outbound request includes:
  - `X-InfraLynx-Event-Id`
  - `X-InfraLynx-Event-Type`
  - `X-InfraLynx-Signature-Sha256`

## Signature model

The delivery payload is JSON. InfraLynx computes an HMAC SHA-256 signature from the payload body using the webhook secret.

Consumers should:

1. read the raw request body
2. compute the same HMAC using the shared secret
3. compare the result to `X-InfraLynx-Signature-Sha256`

## Known limitations

- secrets are stored as bootstrap platform data, not in a dedicated secret manager
- there is no IP allowlist model yet
- there is no replay-prevention token yet
- token-based outbound auth is deferred

These gaps are tracked as follow-up work, not hidden assumptions.
