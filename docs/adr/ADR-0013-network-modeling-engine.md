# ADR-0013 Network Modeling Engine

## Title

Network Modeling Engine

## Status

Accepted

## Context

InfraLynx now has core, IPAM, DCIM, and cross-domain binding contracts. The platform needs a deterministic way to model topology relationships and trace simple paths without jumping directly into a full graph engine.

## Decision

InfraLynx will introduce topology and path-tracing helpers inside `@infralynx/network-domain`.

The initial implementation will:

- model topology as explicit directed edges
- distinguish L2, L3, VLAN, and cable relationships by edge kind
- use breadth-first traversal with stable ordering
- bound traversal with a caller-provided depth limit

## Consequences

Benefits:

- deterministic and testable topology behavior
- clear separation between physical, VLAN, and routed relationships
- lower implementation risk than introducing a full graph platform early

Tradeoffs:

- limited support for advanced routing scenarios
- no weighted path selection yet
- future scaling work will be required for very large topologies
