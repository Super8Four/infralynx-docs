# API Versioning

InfraLynx exposes versioned API contracts under `/api/v1`.

## Rules

- All new integrations must target `/api/v1`.
- Contract changes that break compatibility require a new major API namespace.
- Backward-compatible additions may ship within the active version.
- Legacy unversioned `/api/*` routes are compatibility shims only.

## Response Metadata

Versioned JSON responses include a `meta` object:

```json
{
  "meta": {
    "apiVersion": "v1",
    "deprecated": false
  }
}
```

This metadata is appended consistently so clients can distinguish stable versioned responses from legacy compatibility traffic.

## Compatibility Expectations

- New fields may be added to JSON responses in a backward-compatible way.
- Existing field semantics must not change without a version bump.
- Request validation is enforced before handlers run on versioned routes.
- Legacy routes may emit deprecation headers before removal.
