# ADR-0022: Import Export Framework

## Status

Accepted

## Context

InfraLynx needs a consistent transfer layer for CSV, JSON, and API-based bulk operations across multiple domains. The platform also needs dry-run validation, clean error reporting, and a path to asynchronous import execution through the job engine.

## Decision

InfraLynx will implement import and export as a standalone transfer service with:

- dataset-owned transfer schemas
- transport-neutral validation rules
- explicit CSV, JSON, and API format support
- synchronous commit for small valid payloads
- job-engine-backed asynchronous import for larger batches
- file-backed transfer state as the bootstrap runtime

## Consequences

Transfer behavior is now centralized and consistent across formats. The current implementation is operational for bootstrap workflows, while later chunks can replace file-backed transfer state with domain-aware persistence and richer rollback behavior without breaking the import/export contract shape.
