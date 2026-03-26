# DCIM Physical Relationships

The first DCIM design pass focuses on explicit physical relationships rather than operational workflows.

## Physical Topology Rules

- a device may exist in a site without being racked yet
- a cable must terminate on two distinct endpoints
- front and rear rack faces are independent occupancy planes
- interface and power relationships are separate concerns and must not be conflated

## Relationship Types

### Rack Occupancy

- device to rack
- bounded by rack unit count
- face-aware

### Data Connectivity

- interface to interface through a cable
- modeled as physical connectivity only

### Power Connectivity

- power port to power endpoint through a power cable
- tracked separately from data ports

## Deferred Concerns

Later chunks should add:

- modules and child device relationships
- port breakout modeling
- path tracing across cables and patch points
- structured power feeds and upstream source modeling
