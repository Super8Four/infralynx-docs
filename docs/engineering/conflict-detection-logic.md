# Conflict Detection Logic

The conflict engine operates on the candidate post-mutation state rather than the raw incoming payload.

## Why

This avoids drift between dry-run behavior and committed writes. InfraLynx first constructs the record that would be saved, then validates the resulting inventory snapshot.

## IPAM Conflicts

- `prefix_overlap`
  Returned when two sibling or unrelated prefixes overlap in the same VRF.
- `prefix_undeclared_containment`
  Returned when one prefix contains another but the hierarchy is not declared through `parentPrefixId`.
- `prefix_outside_parent`
  Returned when a child prefix is not actually inside its declared parent.
- `ip_overlap`
  Returned when the same host address appears more than once in the same VRF.
- `ip_outside_prefix`
  Returned when an IP address falls outside its linked prefix.

## DCIM And Relationship Conflicts

- `device_missing_site`
- `device_missing_rack`
- `device_rack_site_mismatch`
- `interface_missing_device`
- `connection_missing_*`
- `connection_*_mismatch`

These checks keep cross-domain references explicit and prevent broken relationship graphs from being persisted.

## Warnings

Warnings are non-blocking. In the bootstrap validation engine, IPv6 overlap analysis is reported as a warning rather than a hard failure because the current engine is focused on the active IPv4-heavy control plane.
