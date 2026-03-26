# ADR-0007: Database Abstraction Design

- Title: Database Abstraction Design
- Status: Accepted

## Context

InfraLynx must support PostgreSQL, Microsoft SQL Server, and MariaDB without treating vendor-specific SQL as a portable default. Early implementation work needs a stable design contract for engine support, migration layout, and CI expectations before runtime adapters are built.

## Decision

InfraLynx will:

- treat PostgreSQL as the reference engine
- create a dedicated `@infralynx/db-abstraction` package for engine profiles, capability mapping, and migration rules
- store migrations in engine-specific directories named `postgres`, `mssql`, and `mariadb`
- keep migration versions aligned across supported engines
- introduce an engine-matrix GitHub workflow that validates abstraction and migration layout before full database execution testing exists

## Consequences

- engine support becomes an explicit architectural contract instead of an implicit assumption
- migration design must account for engine-specific DDL, JSON, and parameter-binding differences
- later database runtime work can extend the abstraction package instead of inventing compatibility rules ad hoc
- CI can evolve from structural validation to container-backed engine execution without changing the repository model
