# Validation Rules

InfraLynx validates candidate inventory mutations before they are written.

## Write Gate

- Validation runs before `create` and `update` operations.
- Failed validation blocks persistence.
- Dry-run validation uses the same mutation planning path as the real write flow.

## Current Rule Areas

- Prefix parent-child relationships must be explicit and internally consistent.
- Prefixes in the same VRF cannot overlap unless the overlap is a declared parent-child containment relationship.
- IP addresses in the same VRF cannot duplicate the same host address.
- IP addresses must stay inside their declared prefix when a prefix link is provided.
- Devices must reference existing sites.
- Device rack placement must reference an existing rack in the same site.
- Interfaces must reference existing devices.
- Connections must reference existing devices and interfaces, and interface ownership must match the endpoint device IDs.

## Validation Output

InfraLynx returns:

- field errors for malformed or incomplete input
- conflicts for cross-record integrity problems
- warnings for non-blocking conditions

Conflicts are returned separately so callers can distinguish bad payload shape from data collisions.
