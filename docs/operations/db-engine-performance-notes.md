# DB Engine Performance Notes

InfraLynx keeps PostgreSQL as the reference engine for query planning and indexing behavior, but the supported engine set includes PostgreSQL, Microsoft SQL Server, and MariaDB.

## PostgreSQL

- treat `EXPLAIN (ANALYZE, BUFFERS)` as the reference review path
- plan for native network-aware types later where IPAM persistence requires them
- prefer `IF NOT EXISTS` on shared index migrations where available

## Microsoft SQL Server

- validate with actual execution plans plus `SET STATISTICS IO, TIME ON`
- use include columns selectively when a query shape proves it needs coverage
- check sort spill risk on filtered list pages

## MariaDB

- validate with `EXPLAIN FORMAT=JSON`
- be conservative with composite indexes because write amplification is easier to hide
- verify collation and string comparison behavior for search-oriented indexes

## Shared Rule

An index that improves one engine but materially harms another does not belong in the shared baseline without an engine-specific note and migration variant.
