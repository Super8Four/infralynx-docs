# Database Testing Plan

InfraLynx database validation expands in phases to keep early CI useful without pretending compatibility has already been proven.

## Initial CI Plan

The first database workflow validates:

- the abstraction package exists and builds
- supported engines are declared explicitly
- migration directories exist for `postgres`, `mssql`, and `mariadb`
- engine-aware workflow matrix execution is in place

## Next Validation Phase

After the runtime data layer exists, CI will add container-backed validation for:

- PostgreSQL
- Microsoft SQL Server
- MariaDB

That phase will test:

- schema application
- migration ordering
- rollback expectations where supported
- engine capability assertions

## Migration Rules

- never assume a PostgreSQL migration is directly portable
- keep migration version numbers aligned across all engines
- document every capability exception before merge
- fail CI when an engine directory or declared engine profile is missing

## Operational Expectation

Database support is not considered production-ready until the matrix validates real migration execution across all supported engines.
