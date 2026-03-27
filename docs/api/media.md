# Media API

The media API provides upload, metadata lookup, linked-object lookup, and binary retrieval.

## Endpoints

- `POST /api/media/upload`
- `GET /api/media/{mediaId}`
- `GET /api/media/{mediaId}/content`
- `GET /api/media/linked?objectType=...&objectId=...&tenantId=...`

## Identity headers

- `X-InfraLynx-Actor-Id`
- `X-InfraLynx-Tenant-Id`
- `X-InfraLynx-Role-Ids`

## Upload payload

```json
{
  "filename": "rack-a1.png",
  "contentType": "image/png",
  "contentBase64": "iVBORw0KGgoAAA...",
  "tenantId": "tenant-ops",
  "associations": [
    { "objectType": "rack", "objectId": "rack-a1" }
  ]
}
```

## Response shape

Metadata responses include:

- media identifiers
- sanitized filename
- content type and size
- tenant ownership
- association links
- content URL

## Contract notes

- media bytes are never embedded in metadata responses
- link lookups are tenant-scoped
- upload and retrieval permissions are enforced separately
