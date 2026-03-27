# Cron Syntax Usage

InfraLynx currently uses a five-field cron format:

`minute hour day-of-month month day-of-week`

Supported patterns in the bootstrap scheduler:

- `*`
- exact numbers
- comma-separated values
- ranges such as `8-18`
- stepped wildcards such as `*/15`
- stepped ranges such as `1-10/2`

Examples:

- `0 6 * * *` runs daily at 06:00 UTC
- `*/15 * * * *` runs every 15 minutes
- `0 9 * * 1-5` runs weekdays at 09:00 UTC

Unsupported in this chunk:

- named months or weekdays
- six-field cron with seconds
- non-UTC schedule execution
