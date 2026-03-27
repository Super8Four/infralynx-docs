# UI Error Handling

InfraLynx separates transport failures from rendering and empty-state behavior.

## Error Strategy

- transport failures are wrapped in a dedicated API client error type
- retryable network errors are surfaced with a retry action
- HTTP failures are reported with status-aware messages
- aborted requests do not transition the UI into a visible failure state

## UI States

- `idle` before the first request is issued
- `loading` while a request is active
- `ready` when normalized data is available
- `error` when a recoverable failure should be shown to the user

## UX Rules

- keep navigation available even during failures
- show loading state without replacing the entire shell
- present one clear retry path
- avoid exposing backend implementation details directly to operators
