# Import And Export Formats

InfraLynx import and export supports three transport formats:

- CSV for operator-friendly tabular exchange
- JSON for structured interchange
- API for direct bulk-operation payloads

## Dataset coverage

The initial baseline supports:

- `tenants`
- `prefixes`
- `sites`

## Format rules

- each dataset has a fixed schema across CSV, JSON, and API transport
- CSV headers must match the documented field order exactly
- JSON imports must be arrays of records
- API imports accept normalized record arrays in the request body

## Export rules

- CSV exports produce one header row plus one row per record
- JSON exports return the dataset record array
- API exports return dataset metadata plus records
