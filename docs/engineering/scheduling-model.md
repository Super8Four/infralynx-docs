# Scheduling Model

InfraLynx schedules are trigger definitions, not execution records.

## Core Rule

The scheduler decides when work should start. The job engine performs the work.

## Stored Schedule Shape

- `id`
- `name`
- `cron_expression`
- `job_type`
- `payload`
- `enabled`
- `last_run`
- `next_run`

## Execution Flow

1. API stores or updates a schedule definition.
2. Worker evaluates due schedules from centralized state.
3. Each due schedule enqueues a normal job.
4. The job engine handles retries, status, and logs.

This keeps scheduling and execution separate and avoids duplicate lifecycle logic.
