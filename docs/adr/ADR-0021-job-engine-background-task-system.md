# ADR-0021: Job Engine Background Task System

## Status

Accepted

## Context

InfraLynx needs asynchronous execution for imports, exports, integrations, and other long-running platform operations. This work must be isolated from API request handling and must avoid early lock-in to a specific queue vendor.

## Decision

InfraLynx will introduce a standalone job engine with:

- explicit job and job-log records
- a queue abstraction separated from worker execution
- API-driven job creation and status retrieval
- dedicated worker processing
- bounded retry handling and explicit failure transitions
- audit-aware lifecycle summaries

## Consequences

Background processing is now a first-class platform capability. The initial file-backed queue implementation is suitable for bootstrap execution and testing, while later chunks can replace the storage and queue backend without breaking the core lifecycle contract.
