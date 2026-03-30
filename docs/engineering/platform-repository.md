# Platform Repository Structure

InfraLynx is intentionally split across a small repository ecosystem so runtime code, documentation, governance, design direction, and infrastructure concerns can evolve without collapsing into a single unstructured repository.

## Repository Ecosystem

- `infralynx-platform` for the runtime application, UI, API, worker, shared packages, tests, and migrations
- `infralynx-docs` for architecture, API, operations, ADRs, onboarding, and public-facing written guidance
- `infralynx-infra` for infrastructure-as-code, deployment pipelines, and hosting configuration
- `infralynx-standards` for governance, contribution policy, templates, and development rules
- `infralynx-design` for UI and UX standards, branding, design-system direction, and shared visual assets

## Current Program Status

- Program snapshot: `v0.1.0-alpha+chunk31`
- Current chunk: `31.1`
- Current phase: `Scale / Reliability`
- Next milestone: `Chunk 32 -> API Versioning`
- Target release: `v1.0.0`

## Platform Monorepo

The `infralynx-platform` repository is a buildable monorepo foundation designed to keep runtime concerns, shared packages, migrations, and deployment-facing assets separated from the start.

## Structure Overview

- `apps/web` for the user-facing application shell
- `apps/api` for API delivery and request orchestration
- `apps/worker` for asynchronous processing and integrations
- `packages/config` for shared configuration metadata and helpers
- `packages/core-domain` for base entities, statuses, permissions, and roles
- `packages/auth` for identity, session, and authorization scaffolds
- `packages/audit` for audit record contracts
- `packages/cache-core` for Redis-backed caching abstractions, TTL policies, and invalidation helpers
- `packages/db-performance` for pagination standards, query review metadata, and index strategy helpers
- `packages/media-core` for media metadata, validation, linking, and access-control helpers
- `packages/media-storage` for filesystem and future cloud-backed object storage adapters
- `packages/event-core` for explicit integration event records
- `packages/webhooks` for webhook configuration and delivery contracts
- `packages/job-core` for job lifecycle, retry, and job-log contracts
- `packages/job-queue` for queue abstraction and file-backed queue persistence
- `packages/scheduler` for recurring schedule definitions, cron parsing, and job-trigger orchestration
- `packages/backup` for backup archive, restore preview, and data-safety orchestration
- `apps/api/src/cache` for API-side cache orchestration, scoped keys, and invalidation boundaries
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
- `packages/media-core` defines media metadata, linking, and tenant-aware access contracts
- `packages/media-storage` defines object storage adapters and must not own metadata policy
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

## Navigation Integration Layer

Navigation is split across three ownership areas:

- `packages/ui/src/navigation` for route metadata, grouping, breadcrumb, and context contracts
- `apps/web/src/layout` for shell composition and structural layout ownership
- `apps/web/src/components/layout/navigation` for sidebar, breadcrumb, and context navigation rendering

This keeps navigation rules centralized and prevents individual pages from inventing inconsistent hierarchy behavior.

## Data Interaction Layer

Phase 1 CRUD and read-only resource interaction is split across four ownership areas:

- `apps/api/src/inventory` for persisted inventory contracts, list/detail payloads, and CRUD mutation handling
- `apps/web/src/services` for API transport and normalization
- `apps/web/src/pages/*` for resource-level list, detail, and form composition
- `apps/web/src/components/forms`, `apps/web/src/components/tables`, and `apps/web/src/components/detail` for reusable interaction primitives

This keeps the UI decoupled from storage details and keeps CRUD behavior consistent across domains.

## Media Service Layer

Media handling is split across three ownership areas:

- `packages/media-core` for metadata, links, validation, and RBAC-aware access checks
- `packages/media-storage` for storage adapters
- `apps/api/src/media` for HTTP upload and retrieval endpoints

This keeps file handling independent from UI code and prevents domain models from owning file storage concerns.

## Job Engine Layer

Background work is split across four ownership areas:

- `packages/job-core` for job records, state transitions, retry rules, and log contracts
- `packages/job-queue` for queue storage and leasing behavior
- `apps/api/src/jobs` for HTTP job creation and status retrieval
- `apps/worker/src/jobs` for asynchronous processing and handler execution

This keeps asynchronous execution separate from request handling and prevents domain packages from owning queue infrastructure.

## Scheduler Layer

Recurring and timed trigger behavior is split across three ownership areas:

- `packages/scheduler` for schedule contracts, cron parsing, next-run calculation, and persisted schedule state
- `apps/api/src/scheduler` for schedule CRUD and visibility endpoints
- `apps/worker/src/jobs` for due-schedule evaluation and job enqueueing

This keeps the scheduler focused on trigger creation and leaves execution to the job engine.

## Backup And Restore Layer

Backup and restore behavior is split across three ownership areas:

- `packages/backup` for archive creation, restore validation, restore rollback safety, and engine strategy contracts
- `apps/api/src/backup` for HTTP backup management and restore endpoints
- `apps/worker/src/jobs` for asynchronous scheduled backup execution

This keeps data-safety flows centralized and prevents restore logic from leaking into domain packages.

## Query And Index Strategy Layer

Database performance planning is split across three ownership areas:

- `packages/db-performance` for pagination standards, critical query reviews, explain-plan guidance, and index definitions
- `migrations/postgres`, `migrations/mssql`, and `migrations/mariadb` for engine-specific index migrations
- `apps/api/src/inventory` and `apps/api/src/index.ts` for applying shared pagination and deterministic sort behavior on active read surfaces

This keeps performance rules explicit before the persistent database adapters land and avoids scattering query semantics across unrelated packages.

## Import And Export Layer

Transfer behavior is split across three ownership areas:

- `packages/data-transfer` for schema rules, parsing, validation, and file-backed transfer state
- `apps/api/src/import` for validation, commit, and async-import endpoints
- `apps/api/src/export` for format-aware export endpoints

This keeps transport formats consistent across domains and prevents ad hoc import logic from leaking into runtime services.

## Event And Webhook Layer

Integration events are split across four ownership areas:

- `packages/event-core` for stored event contracts
- `packages/webhooks` for webhook configuration, filtering, signing, and delivery records
- `apps/api/src/webhooks` for event and webhook HTTP endpoints plus emission orchestration
- `apps/worker/src/jobs` for asynchronous webhook delivery execution

This keeps outbound integrations explicit and prevents API request handlers from performing direct remote callbacks.
