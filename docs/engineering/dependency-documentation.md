# Dependency Documentation

Chunk 22.5 standardized the platform around wrapped external libraries for infrastructure concerns.

## Auth

- `openid-client` for OIDC flows
- `ldapjs` for LDAP and Active Directory connectivity
- `passport-saml` for SAML request and response handling
- `bcrypt` for password hashing
- `jose` retained for JWT session handling

## Background Processing

- `bullmq` for async jobs, retries, delays, and concurrency
- `ioredis` for Redis connectivity
- `ioredis-mock` for local-compatible BullMQ development and test flows
- `node-cron` for recurring schedule triggers

## Integration and Media

- `axios` for outbound webhook delivery
- `multer` for multipart upload parsing

## UI

- `reactflow` for topology graph rendering

## Dependency Governance Notes

- Libraries are used only through InfraLynx-owned packages or runtime adapters.
- Replacements must update documentation, changelog, and versioning together.
- Dependency choice does not override InfraLynx data models or domain boundaries.
