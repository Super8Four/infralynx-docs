# API Error Model

InfraLynx versioned endpoints use a standardized JSON error envelope.

## Shape

```json
{
  "error": {
    "code": "invalid_body",
    "message": "request body failed validation",
    "details": {}
  },
  "meta": {
    "apiVersion": "v1",
    "deprecated": false
  }
}
```

## Required Fields

- `error.code`: stable machine-readable classification
- `error.message`: human-readable summary
- `meta.apiVersion`: current API namespace
- `meta.deprecated`: deprecation marker for the response contract

## Typical Error Codes

- `invalid_json`
- `invalid_query`
- `invalid_body`
- `not_found`
- `forbidden`
- `unauthorized`
- `response_contract_violation`

## Guidance

- Clients should branch on `error.code`, not `error.message`.
- Validation failures may include structured `details`.
- Server-side contract failures should be treated as platform defects, not user input problems.
