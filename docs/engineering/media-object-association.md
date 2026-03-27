# Media Object Association Model

InfraLynx media relationships are modeled through explicit links.

## Media record

- `id`
- `filename`
- `content_type`
- `size`
- `storage_path`
- `tenant_id`
- `created_by`
- `created_at`

## Media link record

- `media_id`
- `object_type`
- `object_id`

## Supported object types

- tenant
- device
- rack
- site

## Design rule

Domains reference media through links. They do not store direct media fields or embedded file metadata in their own contract models.
