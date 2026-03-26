# DCIM Data Model

The InfraLynx DCIM baseline starts with six physical domain entities:

- site
- rack
- device
- interface
- power port
- cable

These contracts are defined in `@infralynx/dcim-domain`.

## Entity Relationships

- a site contains many racks and devices
- a rack belongs to one site
- a device belongs to one site and may optionally occupy one rack position
- interfaces and power ports belong to one device
- cables connect two distinct endpoints

## Core Models

### Site

- `id`
- `slug`
- `name`
- `tenantId`

### Rack

- `id`
- `siteId`
- `name`
- `totalUnits`

### Device

- `id`
- `siteId`
- `rackPosition`
- `name`
- `role`
- `status`

### Interface

- `id`
- `deviceId`
- `name`
- `kind`
- `enabled`

### Power Port

- `id`
- `deviceId`
- `name`
- `feedKind`

### Cable

- `id`
- `kind`
- `aSide`
- `zSide`
- `status`

## Boundary Rules

- rack occupancy is optional and must stay explicit
- physical topology should be expressed through cables, not inferred from port naming
- site and rack placement must remain separate from logical network relationships
