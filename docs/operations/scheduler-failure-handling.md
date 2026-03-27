# Scheduler Failure Handling

InfraLynx treats scheduling failures and job failures differently.

## Scheduler Responsibility

- persist schedule definitions
- compute `next_run`
- enqueue jobs when schedules become due

## Job Engine Responsibility

- execute work
- retry failed jobs
- record execution logs
- expose final job state

## Missed Run Behavior

In the bootstrap model, due schedules are evaluated on worker polling. If the worker is down, the schedule remains due and is enqueued on the next successful poll after restart.

This favors durability over exact-time guarantees and can lead to delayed execution, but not silent loss.
