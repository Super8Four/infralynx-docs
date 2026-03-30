# ADR-0032: Backup Restore Data Safety

## Status

Accepted

## Context

InfraLynx now has multiple file-backed control-plane services that hold operational state. The platform needs a consistent backup and restore mechanism before broader production exposure, but the long-term database-backed platform is still in progress.

## Decision

InfraLynx will implement a centralized backup service that:

- protects the active `runtime-data` persistence layer now
- supports full and partial section backups
- validates restores before applying them
- performs rollback-safe restore operations
- integrates with the scheduler and job engine instead of creating a parallel execution path

The API contract keeps the backup engine explicit so future PostgreSQL, SQL Server, and MariaDB native backup strategies can replace the bootstrap implementation without breaking callers.

## Consequences

Positive:

- the platform now has a working recovery path
- restore operations are validated instead of blindly replayed
- scheduler integration makes recurring protection possible immediately

Tradeoffs:

- current backup storage is still file-backed
- database-native tooling is documented, not yet active
- large datasets will require retention and optimization work later
