# IPAM Hierarchy Rules

InfraLynx renders IPAM as a strict prefix tree grouped by VRF.

## Required Rules

- every child prefix must reference an explicit parent prefix ID
- parent and child prefixes must remain in the same VRF
- child prefixes must always be more specific than their parent
- hierarchy cycles are invalid
- prefixes without a parent are treated as VRF roots

## Rendering Implications

- VRFs are the first grouping level
- prefixes are rendered in deterministic specificity order
- utilization is precomputed before the tree is handed to the UI

## Why These Rules Exist

The hierarchy view is only useful if nesting is authoritative. The UI must not guess parentage or sort relationships from CIDR strings alone.
