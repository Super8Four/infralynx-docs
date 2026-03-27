# Topology Node and Edge Mapping Rules

InfraLynx maps topology visuals from explicit infrastructure records rather than inferred network guesses.

## Node Mapping

Each rendered node represents one device.

Required node fields:

- device ID
- device name
- device role
- site ID and site name
- device tone
- interface count
- VLAN IDs

Node positions are derived from deterministic layout rules:

- site determines the horizontal region
- role determines the vertical band
- name and ID determine stable ordering within a band

## Edge Mapping

Each rendered edge represents an explicit relationship between two devices.

Supported edge kinds:

- `cable-link`
- `l2-adjacency`
- `l3-adjacency`
- `vlan-propagation`

Required edge fields:

- edge ID
- source device ID
- target device ID
- edge kind
- label
- VLAN IDs

## Filtering Rules

- site filter removes nodes outside the selected site and drops orphaned edges
- role filter removes nodes that do not match the selected role and drops orphaned edges
- VLAN filter keeps only nodes and edges explicitly tagged with the selected VLAN

The UI never reconstructs hidden links after filtering. If a node or edge is filtered out, it is absent from the rendered graph.
