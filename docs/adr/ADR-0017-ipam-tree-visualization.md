# ADR-0017: IPAM Tree Visualization

## Title

IPAM Tree Visualization

## Status

Accepted

## Context

InfraLynx needs an operator-facing IPAM view that exposes VRF boundaries, prefix nesting, and allocation pressure without forcing users to reconstruct hierarchy from flat lists.

The platform already has:

- VRF, prefix, IP address, and VLAN contracts
- baseline allocation rules
- a UI shell capable of API-backed visualization stages

What was missing was a deterministic hierarchy model and a browser surface that could render it efficiently.

## Decision

InfraLynx will implement IPAM visualization with three layers:

1. `@infralynx/ipam-domain` validates hierarchy and precomputes prefix utilization
2. `@infralynx/ui` converts validated hierarchy into a reusable tree model and flattened row set
3. `apps/web` renders the expandable tree and prefix detail panel

The initial tree view will:

- group by VRF
- support expand and collapse
- render prefix utilization indicators
- keep selection and interaction logic in the web layer

## Consequences

Positive:

- hierarchy validation remains a domain concern
- UI rendering stays fast by consuming precomputed rows
- utilization is visible directly in the tree without extra reporting steps

Negative:

- very large trees may still need virtualization later
- utilization estimates are intentionally conservative for large prefixes
- branch editing and drag-reparenting remain out of scope
