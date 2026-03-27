# Job Lifecycle Model

InfraLynx jobs move through a bounded lifecycle.

## Lifecycle states

- `pending`: the job has been accepted and is waiting to be leased by a worker
- `running`: a worker has leased the job and is currently executing it
- `success`: execution completed successfully and produced a terminal result
- `failed`: execution exhausted retry allowance or hit a terminal failure condition

## Transition rules

- API creation always starts at `pending`
- worker leasing moves a job from `pending` to `running`
- successful handler completion moves a job from `running` to `success`
- handler failure either returns the job to `pending` for retry or moves it to `failed`

## Retry accounting

- every failed execution attempt increments `retryCount`
- retry policy is explicit and attached to the job contract
- jobs stop retrying when the retry cap is reached
- terminal failure preserves the latest error message in the job result metadata
