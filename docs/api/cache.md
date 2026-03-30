# Cache API

InfraLynx currently exposes a lightweight cache status endpoint for operational visibility.

## Endpoints

### `GET /api/cache/status`

Returns:

- current cache backend
- namespace
- configured default TTL profiles
- generation timestamp

## Notes

- cache entries are internal implementation details and are not individually enumerable through the API
- cache invalidation is triggered automatically by successful write operations
- cache is an optimization layer only; responses remain valid when the cache is cold or unavailable
