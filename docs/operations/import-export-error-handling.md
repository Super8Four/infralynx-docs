# Import And Export Error Handling

InfraLynx transfer failures must return actionable diagnostics without partial silent mutation.

## Error handling rules

- parse failures return document-level errors
- row validation failures return row and field details
- invalid commits do not mutate transfer state
- dry-run mode returns the same validation model as commit mode

## Async import rules

- large imports can be queued as jobs
- queued imports return a job record immediately
- final execution state is tracked through the job engine
- retry handling follows the platform job lifecycle rules

## Operational guidance

- operators should validate before committing large imports
- failed imports should be reviewed using both validation output and job logs
- rollback strategy for multi-step imports remains a tracked follow-up issue
