# Job System Architecture

InfraLynx background execution is implemented as a standalone platform service.

## Service boundaries

- `@infralynx/job-core` owns job records, lifecycle transitions, retry policy, and job-log contracts
- `@infralynx/job-queue` owns queue persistence and job leasing
- `apps/api/src/jobs` owns HTTP job creation and status retrieval
- `apps/worker` owns asynchronous job execution

## Design rules

- job execution is asynchronous and decoupled from API request latency
- queue behavior is defined behind an abstraction boundary
- workers operate on explicit leased jobs instead of scanning arbitrary domain state
- job status and job logs are persisted separately from the HTTP transport
- audit summaries are emitted alongside lifecycle transitions

## Current implementation

The current baseline uses:

- file-backed queue state
- process-safe file locking for queue mutation
- explicit job and job-log records
- worker-side handler registration by job type
- deterministic status transitions for `pending`, `running`, `success`, and `failed`
