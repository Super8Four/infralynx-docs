# ADR-0025: Scheduled Task System

## Title

Scheduled Task System

## Status

Accepted

## Context

InfraLynx needs recurring and time-based triggers for background work, but job execution logic already exists in the job engine. Re-implementing execution behavior in a scheduler would duplicate status, retry, and logging concerns.

## Decision

InfraLynx will store schedules centrally and evaluate them in the worker runtime. The scheduler only enqueues jobs; it does not execute them. The initial scheduler supports UTC-only five-field cron expressions and persists schedule state in a file-backed store aligned with the existing bootstrap adapters.

## Consequences

- scheduling remains independent from job execution
- retry and failure behavior stay centralized in the job engine
- schedule persistence survives process restarts
- timezone handling is intentionally limited in the bootstrap phase
