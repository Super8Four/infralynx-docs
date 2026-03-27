# Import And Export Validation Rules

InfraLynx validates transfer payloads before commit.

## Validation rules

- dataset name must be recognized
- format must be recognized
- CSV headers must match the expected schema
- required fields must be present
- duplicate IDs are rejected
- prefix records must pass CIDR validation before commit

## Validation behavior

- `POST /api/import/validate` never mutates transfer state
- dry-run mode returns validation results without commit
- invalid commits return structured row and field errors
- large valid commits can be queued through the job engine
