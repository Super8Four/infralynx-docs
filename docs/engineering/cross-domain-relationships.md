# Cross-Domain Relationship Model

InfraLynx uses explicit ID-based relationships across domains. Domain packages own their own entities, while cross-domain packages define the bindings between them.

## Relationship Rules

- relationships are explicit, not inferred from naming or topology
- IDs are used instead of embedded objects across package boundaries
- domain packages keep ownership of their own entities
- cross-domain logic lives in dedicated integration contracts, not inside app runtimes

## Current Relationship Set

- device to interface through `dcim-domain`
- interface to IP address through `network-domain`
- interface to VLAN through `network-domain`
- cable to interface through `network-domain`
- VRF to prefix to IP hierarchy through `ipam-domain` and `network-domain`

## Package Ownership

- `@infralynx/dcim-domain` owns physical entities and cable/device primitives
- `@infralynx/ipam-domain` owns VRFs, prefixes, IP addresses, and VLANs
- `@infralynx/network-domain` owns cross-domain bindings and validation helpers

## Integration Boundaries

- `dcim-domain` knows interface-local references such as cable IDs and bound VLAN/IP IDs
- `ipam-domain` knows prefix hierarchy and interface references where the entity naturally owns them
- `network-domain` validates the shape of the cross-domain relationships without embedding domain objects
