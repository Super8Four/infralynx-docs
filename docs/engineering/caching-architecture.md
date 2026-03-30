# Caching Architecture

InfraLynx uses a centralized cache layer for API-owned read optimization. Redis is the primary backing store, and a mock Redis adapter is used for local bootstrap and tests when `INFRALYNX_REDIS_URL` is not configured.

## Principles

- cache infrastructure is wrapped behind `@infralynx/cache-core`
- domain packages do not call Redis directly
- cache keys are scoped at the API layer
- writes always own invalidation
- cache is an optimization, never a source of truth

## Current Cached Surfaces

- `/api/overview`
- `/api/search`
- `/api/racks/demo`
- `/api/topology/demo`
- `/api/ipam-tree/demo`
- inventory navigation, list, and detail reads
- auth provider reads
- auth session status
- RBAC summary and RBAC admin snapshot

## Request Scoping

User-sensitive responses use a request fingerprint derived from bearer token or InfraLynx actor headers. This prevents permission-sensitive data from leaking across callers while still allowing repeated reads to reuse cached payloads.

## Store Strategy

- production target: Redis
- local fallback: mock Redis
- invalidation strategy: namespace and prefix deletion
- payload format: JSON
