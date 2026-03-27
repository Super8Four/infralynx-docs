# Import And Export API

InfraLynx exposes standardized transfer endpoints for CSV, JSON, and API-based bulk operations.

## Import endpoints

- `POST /api/import/validate`
- `POST /api/import/commit`

## Export endpoints

- `GET /api/export/{dataset}?format=json`
- `GET /api/export/{dataset}?format=csv`
- `GET /api/export/{dataset}?format=api`

## Datasets

- `tenants`
- `prefixes`
- `sites`

## Request model

Import requests include:

- `dataset`
- `format`
- `dryRun`
- `async`
- `csvContent`, `jsonContent`, or `records`

## Response model

Responses include:

- validation status
- record count
- structured errors and warnings
- commit mode (`sync` or `async`)
- queued job details for async imports
