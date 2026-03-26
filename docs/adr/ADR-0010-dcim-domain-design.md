# ADR-0010: DCIM Domain Design

- Title: DCIM Domain Design
- Status: Accepted

## Context

InfraLynx needs a stable DCIM contract before topology, device management, and path-tracing features can be implemented. Sites, racks, devices, interfaces, power, and cabling form the physical foundation for later networking and inventory features.

## Decision

InfraLynx will introduce an `@infralynx/dcim-domain` package that defines:

- site, rack, device, interface, power-port, and cable models
- rack-position validation helpers
- rack occupancy checks
- cable endpoint validation

The first chunk remains at the schema and relationship layer and defers richer hardware lifecycle behavior.

## Consequences

- later DCIM work can extend stable physical contracts instead of inventing them inside app runtimes
- rack modeling and cabling rules become testable early
- physical and logical relationships remain clearly separated
- more advanced modeling such as modules, path tracing, and power-chain topology remains deferred
