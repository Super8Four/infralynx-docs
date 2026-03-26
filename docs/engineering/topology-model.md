# Topology Model

InfraLynx models topology as explicit directed edges between stable IDs. The model stays deliberately small so it can support deterministic validation and tracing before a larger graph subsystem exists.

## Node Classes

- DCIM interfaces
- IP addresses
- prefixes
- VLANs

## Edge Classes

- `l2-adjacency`
- `l3-adjacency`
- `vlan-propagation`
- `cable-link`

## Modeling Rules

- edges always connect two distinct node IDs
- edge kinds are explicit and never inferred from naming
- metadata is supplemental and does not replace typed IDs
- traversal order is deterministic and derived from stable edge sorting

## Ownership

- `dcim-domain` owns physical inventory identifiers
- `ipam-domain` owns logical addressing identifiers
- `network-domain` owns topology edges and traversal helpers

## Current Boundaries

The current model is a scaffold for validation and tracing. It does not yet implement large-topology indexing, path weighting, ECMP handling, or dynamic route computation.
