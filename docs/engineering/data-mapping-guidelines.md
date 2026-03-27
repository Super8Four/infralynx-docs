# Data Mapping Guidelines

Import and export mappings stay explicit and dataset-owned.

## Mapping rules

- transfer records are not embedded into domain models
- transport formats map onto stable transfer schemas first
- API handlers must not bypass transfer validation
- job payloads carry normalized transfer input, not raw multipart state

## Dataset ownership

- tenant transfer records map to core control-plane datasets
- prefix transfer records map to IPAM addressing datasets
- site transfer records map to DCIM location datasets

## Consistency rules

- field names remain consistent across CSV, JSON, and API formats
- null-like optional values are normalized before commit
- schema changes should be captured in ADRs or explicit API documentation updates
