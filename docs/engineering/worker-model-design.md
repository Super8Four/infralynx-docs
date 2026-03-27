# Worker Model Design

InfraLynx workers are independent runtime processes that consume leased jobs from the shared queue abstraction.

## Worker responsibilities

- lease the next pending job
- execute the registered handler for the job type
- write lifecycle updates back to the queue store
- append job logs for significant execution milestones
- emit audit-friendly lifecycle summaries

## Worker design rules

- workers must treat every job as potentially retried
- handlers must be idempotent
- workers must not assume exclusive ownership beyond the active lease
- missing handlers are treated as execution failures, not silent drops

## Current baseline

The current worker runtime provides:

- single-cycle execution for deterministic tests and smoke checks
- loop mode for continuous polling
- handler registration by job type
- bounded retry behavior
- file-backed operational storage that can later be replaced behind the queue abstraction
