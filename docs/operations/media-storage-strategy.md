# Media Storage Strategy

InfraLynx starts with local filesystem storage and a file-backed metadata repository, but the service boundaries are intentionally cloud-ready.

## Current bootstrap strategy

- object bytes stored on local disk
- metadata stored in a file-backed repository
- storage paths scoped by tenant and media ID

## Future adapter direction

- S3-compatible object storage
- Azure Blob storage
- SQL-backed metadata persistence

## Migration rule

Storage adapters must preserve the same media and media-link contract shape so upload, retrieval, and tenant-isolation behavior do not change when backends are swapped.
