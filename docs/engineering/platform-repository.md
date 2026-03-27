# Platform Repository Structure

The `infralynx-platform` repository is a buildable monorepo foundation designed to keep runtime concerns, shared packages, migrations, and deployment-facing assets separated from the start.

## Structure Overview

- `apps/web` for the user-facing application shell
- `apps/api` for API delivery and request orchestration
- `apps/worker` for asynchronous processing and integrations
- `packages/config` for shared configuration metadata and helpers
- `packages/core-domain` for base entities, statuses, permissions, and roles
- `packages/auth` for identity, session, and authorization scaffolds
- `packages/audit` for audit record contracts
- `packages/domain-core` for core platform boundaries and domain contracts
- `packages/shared` for reusable utilities with low coupling
- `tests` for shared testing structure
- `migrations` for engine-specific migration organization
- `deploy` for application deployment-facing assets

## Naming Conventions

- apps are named by runtime role
- packages use singular, purpose-specific names
- directories should describe ownership, not implementation detail
- shared packages must remain intentionally small to avoid accidental coupling

## Boundary Rules

- `apps/*` consume packages and compose runtime behavior
- `packages/domain-core` defines platform-level boundaries and contracts
- `packages/core-domain`, `packages/auth`, and `packages/audit` define reusable platform service contracts
- `packages/ipam-domain` defines VRF, prefix, IP address, VLAN, and allocation contracts
- `packages/dcim-domain` defines site, rack, device, interface, power, and cable contracts
- `packages/network-domain` defines cross-domain bindings, topology edges, and path-tracing helpers
- `packages/ui` defines shell navigation, tokens, and shared UI contracts
- `packages/shared` must not become an unreviewed dumping ground
- database-engine specifics belong under `migrations/*`, not mixed into app code

## UI Integration Layer

The web application uses a three-part data integration boundary:

- `apps/web/src/services` for transport and normalization
- `apps/web/src/hooks` for request lifecycle orchestration
- `apps/web/src/state` for reducer-backed UI state

This keeps frontend rendering decoupled from raw API payload structure.

## Rack Visualization Layer

Rack visualization is split across two ownership areas:

- `packages/ui/src/rack-system` for rack geometry, unit-slot generation, and selection helpers
- `apps/web/src/components/rack` for React rendering and interaction behavior

This keeps positioning logic reusable and prevents rendering components from owning the underlying rack math.

## Topology Visualization Layer

Topology visualization is split across three ownership areas:

- `packages/network-domain/src/topology-view` for deterministic device-node and cable-edge generation
- `packages/ui/src/topology` for graph filtering and selection helpers
- `apps/web/src/components/topology` for rendering and interaction behavior

This keeps graph generation reusable, keeps filters consistent, and prevents the web app from becoming the owner of network topology rules.

## IPAM Tree Visualization Layer

IPAM tree visualization is split across three ownership areas:

- `packages/ipam-domain` for hierarchy validation and utilization helpers
- `packages/ui/src/ipam-tree` for reusable tree models and flattened rows
- `apps/web/src/components/ipam-tree` for rendering and interaction behavior

This keeps hierarchy rules authoritative in the domain layer and prevents the UI from rebuilding prefix trees during rendering.

## Search Integration Layer

Search is split across three ownership areas:

- `packages/core-domain/src/search` for query normalization, matching, ranking, and grouping rules
- `apps/web/src/services/search` for search transport and response normalization
- `apps/web/src/components/search` for global search rendering and grouped result interaction

This keeps the UI decoupled from backend record assembly and prevents domain search logic from fragmenting across multiple frontend components.
