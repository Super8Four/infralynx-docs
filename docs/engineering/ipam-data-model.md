# IPAM Data Model

The InfraLynx IPAM baseline starts with four core entities:

- VRF
- prefix
- IP address
- VLAN

These are modeled as transport-agnostic contracts inside `@infralynx/ipam-domain`.

## Entity Relationships

- a VRF scopes prefixes and IP addresses
- a prefix can optionally belong to a tenant
- a prefix can optionally reference a VLAN for network segmentation context
- an IP address belongs to at most one prefix
- a VLAN can be referenced by many prefixes

## Core Models

### VRF

- `id`
- `name`
- `rd`
- `tenantId`

### Prefix

- `id`
- `vrfId`
- `cidr`
- `family`
- `status`
- `allocationMode`
- `tenantId`
- `vlanId`

### IP Address

- `id`
- `vrfId`
- `address`
- `family`
- `status`
- `role`
- `prefixId`

### VLAN

- `id`
- `vlanId`
- `name`
- `status`
- `tenantId`

## Relationship Rules

- VRF identity must stay stable across all attached prefixes and IP addresses
- IP address family must match the family of the containing prefix
- prefixes and VLAN references are optional but must remain explicit when present
- allocation decisions must operate within a single VRF boundary
