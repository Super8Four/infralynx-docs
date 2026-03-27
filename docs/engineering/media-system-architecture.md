# Media System Architecture

InfraLynx media handling is a core platform service, not a domain-owned feature.

## Service boundaries

- `@infralynx/media-core` owns metadata, object-linking, validation, and RBAC-aware access decisions
- `@infralynx/media-storage` owns object storage adapters
- `apps/api/src/media` owns HTTP transport, header-based identity extraction, and endpoint responses

## Design rules

- media fields are not embedded into domain entities
- file bytes are stored outside the database layer
- media-to-object relationships use an explicit linking model
- tenant boundaries apply to both metadata access and object retrieval

## Current implementation

The current baseline uses:

- file-backed metadata persistence for operational bootstrap
- local filesystem object storage
- explicit media and media-link records
- reusable storage and metadata seams for later SQL and cloud adapters
