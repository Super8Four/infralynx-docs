# Job Retry And Failure Rules

InfraLynx job execution must fail predictably and avoid uncontrolled retry loops.

## Retry rules

- retry limits are explicit and job-scoped
- workers requeue failed jobs only while retry allowance remains
- retry count is recorded on the job record
- repeated failure does not create a duplicate job record

## Failure rules

- terminal failure moves the job to `failed`
- failure details are stored in job result metadata
- job logs must include the failure reason
- audit summaries must record the final failure state

## Operational rules

- handlers must be designed for idempotent re-execution
- failure alerting is a follow-up concern and remains outside the baseline runtime
- queue backends must preserve job status and logs across worker restarts
