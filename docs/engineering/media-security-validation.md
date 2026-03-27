# Media Security And Validation Rules

InfraLynx media upload handling must reject unsafe input before persistence.

## Validation baseline

- filename is sanitized before storage
- content type must be on the allow list
- file size must be positive and under the configured maximum
- object links must use supported object types and non-empty IDs

## Current allow list

- `image/png`
- `image/jpeg`
- `image/gif`
- `image/webp`
- `application/pdf`
- `text/plain`

## Access control rules

- media endpoints require actor, tenant, and role headers
- `media:write` is required for upload
- `media:assign` is required when creating object links
- `media:read` is required for metadata and content retrieval
- tenant isolation blocks cross-tenant access even when a record exists
