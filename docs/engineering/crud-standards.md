# CRUD Standards

Phase 1 CRUD in InfraLynx is API-driven and resource-oriented.

## Required Views

Each writable resource must expose:

- list view with sortable columns
- basic filtering
- pagination-ready response contracts
- create form
- detail view
- edit form
- delete flow with confirmation

## API Rules

- The UI must call API endpoints for all mutations.
- The UI must not write directly to local domain stores.
- Detail views must consume explicit related-object payloads from the API.
- Validation failures must return field-level errors when possible.

## UI Rules

- Forms must enforce required fields before submit.
- Tables must use stable column definitions.
- Detail pages must show object identity and relationship context first.
- Delete must be blocked when referential integrity would be broken.

## Bootstrap Persistence Rule

The Phase 1 CRUD layer uses a local file-backed inventory store as a temporary persistence model. This is acceptable only because:

- the service boundary is explicit
- the UI is decoupled from storage details
- future database-backed persistence can replace the adapter without changing page contracts
