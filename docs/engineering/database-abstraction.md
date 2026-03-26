# Database Abstraction Design

InfraLynx supports three SQL engines:

- PostgreSQL
- Microsoft SQL Server
- MariaDB

PostgreSQL is the reference engine. Other engines must match the product contract through explicit capability mapping rather than implicit SQL portability assumptions.

## Abstraction Layer

The abstraction layer is owned by `@infralynx/db-abstraction` in the platform monorepo.

Its initial responsibilities are:

- define supported engine identifiers
- record capability status per engine
- define migration rules and engine profiles
- make engine-specific constraints visible before runtime adapters are implemented

## Compatibility Matrix

| Capability | PostgreSQL | SQL Server | MariaDB | Notes |
| --- | --- | --- | --- | --- |
| Transactional DDL | Native | Restricted | Restricted | DDL rollback assumptions must not be shared blindly across engines. |
| JSON document columns | Native | Emulated | Emulated | PostgreSQL is the canonical JSON behavior reference. |
| Generated or computed columns | Native | Native | Native | Syntax and semantics differ and must be isolated in engine-specific migrations. |
| Parameter binding | `$1`, `$2`, ... | `@p1`, `@p2`, ... | `?` | Query compilation must remain dialect-aware. |
| Identifier quoting | `\"name\"` | `[name]` | `` `name` `` | SQL generation must never hard-code a single quoting model. |

## Design Rules

- application code must depend on capability contracts, not engine-specific SQL
- vendor-specific features require an explicit design note before adoption
- engine behavior that cannot be normalized must be marked as restricted
- reference-engine behavior does not imply portable DDL or query semantics

## Migration Strategy

- keep one shared migration version stream
- store SQL per engine in parallel engine directories
- document intentional deviations from the PostgreSQL reference migration
- isolate destructive changes so rollback expectations stay explicit

## Engine-Specific Considerations

### PostgreSQL

- default reference for schema behavior
- canonical JSON semantics
- baseline for new abstraction features

### Microsoft SQL Server

- JSON is function-oriented rather than backed by a dedicated JSON type
- DDL transaction behavior must be reviewed per migration
- naming, quoting, and parameter models differ materially from PostgreSQL

### MariaDB

- JSON handling differs from PostgreSQL expectations
- DDL rollback characteristics require defensive migration design
- dialect differences must be isolated in engine-specific SQL files
