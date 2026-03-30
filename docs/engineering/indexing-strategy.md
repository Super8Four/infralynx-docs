# Indexing Strategy

InfraLynx treats indexing as an explicit contract, not a database-side afterthought. Every index must map to a real filter-plus-sort query shape that exists in the API or background-processing surface.

## Principles

- index against concrete query shapes, not theoretical future reads
- prefer composite indexes that match filter order and pagination sort order
- keep PostgreSQL as the reference engine, then document MSSQL and MariaDB deviations
- review write-side cost before promoting an index into the shared engine baseline

## Current Priority Indexes

- tenant-scoped site lookup and listing
- site-scoped rack listing
- site and role filtered device listing
- VRF and parent-scoped prefix reads
- prefix-scoped IP address reads
- auth provider, session, and RBAC grant expansion reads
- audit and job timeline reads

## Review Rule

If a query cannot name the index it expects to use, it is not ready for a shared migration.
