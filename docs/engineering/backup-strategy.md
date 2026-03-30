# Backup Strategy

InfraLynx currently runs on a bootstrap file-backed persistence layer under `runtime-data`. The backup service protects that active state directly while keeping the service abstraction aligned to the future database-backed platform.

## Current Strategy

- Full backups capture all supported runtime sections.
- Partial backups capture only the requested sections.
- Archives are stored as compressed JSON snapshots.
- Backup metadata is stored separately from the archived payload.
- Backups are created through the API or the job engine, not by direct UI-side file access.

## Supported Sections

- `auth`
- `audit`
- `events`
- `inventory`
- `jobs`
- `media`
- `scheduler`
- `transfers`
- `webhooks`
- `workflows`

## Engine Mapping

PostgreSQL is still the reference database engine for the long-term platform, but the current running system does not yet persist to PostgreSQL, SQL Server, or MariaDB. Until that transition happens, InfraLynx uses:

- `bootstrap-file-store` for working backups
- documented engine strategies for `postgres`, `mssql`, and `mariadb`

The backup service keeps the engine value explicit so the API contract does not need to change when database-native backups replace the bootstrap store.

## Scheduling

Scheduled backups are implemented through Chunk 22 scheduler integration:

- scheduler owns timing
- backup service owns archive creation
- job engine owns asynchronous execution

That separation keeps backup execution consistent with the rest of the platform control plane.
