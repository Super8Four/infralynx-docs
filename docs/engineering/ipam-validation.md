# IPAM Validation Rules

The initial IPAM skeleton validates baseline correctness without implementing full network arithmetic.

## Current Rules

- VLAN IDs must be integers in the range `1-4094`
- route distinguishers must use `ASN:VALUE` shape when present
- prefixes must use CIDR notation
- prefix lengths must stay inside family limits:
  - IPv4: `0-32`
  - IPv6: `0-128`
- IP addresses must include host prefix length notation
- child prefix requests must remain in the same family and VRF as the parent prefix
- child prefixes must be more specific than the parent prefix
- allocation can only occur from active parent prefixes

## Deferred Validation

The following are intentionally deferred until later implementation chunks:

- full IPv4/IPv6 containment math
- overlap detection across sibling prefixes
- usable-host calculations
- gateway reservation strategy
- duplicate address detection across persisted records
