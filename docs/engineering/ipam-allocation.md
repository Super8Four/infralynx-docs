# IPAM Allocation Logic

InfraLynx starts with an explicit allocation-policy model before implementing a runtime allocator.

## Allocation Modes

- `hierarchical`
- `pool`
- `static`

## Baseline Logic

The current design treats allocation as valid when:

- parent and child prefixes use the same address family
- parent and child prefixes stay within the same VRF
- the child prefix is more specific than the parent prefix
- the parent prefix is active

## Design Constraints

- allocation rules must be deterministic and auditable
- VRF boundaries must never be crossed by allocator logic
- later host-allocation logic must be derived from prefix contracts, not embedded in app runtimes
- pool behavior should be added by extending `allocationMode`, not by creating parallel ad hoc workflows

## Next Implementation Phase

Later IPAM chunks should add:

- overlap detection
- prefix utilization metrics
- host allocation from parent pools
- reserved-range handling
- database persistence and query boundaries
