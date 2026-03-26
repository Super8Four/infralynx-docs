# L2 vs L3 Handling

InfraLynx distinguishes layer 2 and layer 3 relationships explicitly so topology consumers can reason about switching and routing behavior without guessing intent from raw connections.

## Layer 2

Layer 2 relationships represent adjacency and propagation at the switching layer.

- `cable-link` captures a physical connection
- `l2-adjacency` captures a switching adjacency between interfaces
- `vlan-propagation` captures VLAN movement across an eligible link or interface boundary

## Layer 3

Layer 3 relationships represent addressing and routed adjacency.

- `l3-adjacency` links an interface or routed hop to an IP-level node
- VRF, prefix, and IP hierarchy remain explicit and ID-based

## Separation Rules

- L2 edges do not imply L3 reachability
- L3 edges do not imply physical adjacency
- VLAN membership does not embed interface objects
- routing and switching relationships can coexist on the same inventory objects

## Example Scenario

An interface can:

- participate in a `cable-link`
- form an `l2-adjacency`
- propagate one or more VLANs
- bind to one or more IP addresses through separate `l3-adjacency` edges

This keeps physical, broadcast, and routed semantics separate while still allowing end-to-end tracing.
