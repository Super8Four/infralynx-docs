# Path Tracing Logic

The first InfraLynx path-tracing engine is intentionally deterministic and breadth-first. Its purpose is to define the traversal contract, not to solve every networking scenario in the first iteration.

## Trace Inputs

- start node ID
- target node ID
- allowed edge kinds
- maximum depth

## Trace Behavior

1. Build an adjacency index from topology edges.
2. Sort outbound edges into a stable order.
3. Traverse with breadth-first search.
4. Stop when the target node is reached or the depth limit is exceeded.

## Determinism Rules

- the same edge set must produce the same traversal order
- visited node tracking prevents loops
- depth limiting bounds recursion and runtime cost
- edge-kind filters let callers trace only the layers they care about

## Near-Term Use Cases

- validate direct L2 and L3 service reachability
- prove that an interface-to-address binding can be traversed
- document expected behavior for later topology and path APIs

## Deferred Work

- weighted path selection
- multi-path tracing
- policy-based routing interpretation
- large-topology performance indexing
