# ADR-0009: IPAM Domain Design

- Title: IPAM Domain Design
- Status: Accepted

## Context

InfraLynx needs a stable IPAM contract before DCIM, networking, and runtime data services are implemented. VRFs, prefixes, IP addresses, and VLANs are foundational entities that must share consistent relationships and validation rules across the platform.

## Decision

InfraLynx will introduce an `@infralynx/ipam-domain` package that defines:

- VRF, prefix, IP address, and VLAN models
- baseline validation helpers
- allocation-policy helpers for child-prefix eligibility

The first chunk remains at the domain-contract level and defers full address arithmetic, persistence, and allocator implementation.

## Consequences

- later IPAM work can build on stable domain contracts
- validation rules become explicit and testable before storage is implemented
- allocation logic remains visible without prematurely committing to a complex allocator
- richer prefix containment and utilization logic must be added in later chunks
