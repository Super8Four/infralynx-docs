# API Deprecation Policy

InfraLynx uses explicit deprecation signals before removing API behavior.

## Current Policy

- `/api/v1/*` is the active namespace.
- Legacy `/api/*` routes are deprecated compatibility routes.
- Deprecated routes emit deprecation headers and point to this policy.

## Deprecation Process

1. Mark the route or field as deprecated in documentation.
2. Emit deprecation signaling in the API response headers.
3. Preserve a migration window long enough for known consumers to move.
4. Remove the deprecated behavior only in a later versioned API change.

## Integration Expectations

- Consumers should migrate to `/api/v1/*` immediately.
- New consumers should never start on deprecated `/api/*` routes.
- Deprecated compatibility routes may continue to function, but they should not receive new features.
