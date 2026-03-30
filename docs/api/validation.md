# Validation API

## `POST /api/validation/inventory`

Runs dry-run validation for a candidate inventory mutation without persisting it.

### Request Body

```json
{
  "resource": "prefixes",
  "operation": "create",
  "record": {
    "cidr": "10.40.16.0/24",
    "vrfId": "vrf-global",
    "parentPrefixId": "prefix-global-root",
    "status": "active",
    "allocationMode": "pool",
    "tenantId": "tenant-net"
  }
}
```

### Response Shape

```json
{
  "resource": "prefixes",
  "operation": "create",
  "actorId": "user-platform-admin",
  "validation": {
    "valid": false,
    "errors": [],
    "conflicts": [],
    "warnings": []
  },
  "candidateRecord": {}
}
```

## Behavior

- Uses the same mutation-planning path as the inventory write API.
- Returns `400` for field-level validation failures.
- Returns `409` when a candidate would introduce conflicts.
- Returns `200` when the candidate is valid.

## Workflow Integration

Change-control approval requests may include a `validationRequest` payload. InfraLynx validates that candidate before the approval request is created, so invalid changes do not enter the approval queue.
