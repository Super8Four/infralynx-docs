# Restore Procedures

InfraLynx restore is intentionally two-step:

1. validate the selected backup
2. execute the restore only after preview passes

## Restore Flow

1. Query available backups.
2. Run restore validation for the selected backup.
3. Confirm the reported sections and warnings.
4. Execute restore.
5. Re-run platform health and validation checks.

## Safety Controls

- restore validation runs before write operations
- inventory payloads are checked against the validation engine when present
- restore is section-scoped
- rollback copies are created before replacing active data
- failed restores revert to the captured pre-restore state

## Operational Guidance

- prefer partial restore for isolated incidents
- use full restore only for broad corruption or disaster recovery events
- stop active administrative changes before restoring shared runtime sections
- re-check jobs, schedules, and webhook configuration after restore
