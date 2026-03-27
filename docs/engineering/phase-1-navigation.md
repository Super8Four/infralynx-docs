# Phase 1 Navigation

InfraLynx Phase 1 navigation must expose only surfaces that are implemented and usable.

## Navigation Structure

### Core

- Tenants
- Users

### DCIM

- Sites
- Racks
- Devices

### IPAM

- VRFs
- Prefixes
- IP Addresses

### Network

- Interfaces
- Connections

### Operations

- Jobs

## Rules

- Do not expose advanced domains before the underlying workflows are usable.
- Do not mirror the full target product navigation early.
- Keep route naming resource-oriented and stable.
- Keep breadcrumb structure aligned to the sidebar hierarchy.

## Why This Phase Exists

The earlier shell proved out navigation, search, rack visualization, topology, and IPAM views. Phase 1 changes the shell from a capability demo into a usable operator workspace by making navigation track actual CRUD surfaces and currently available operational pages.
