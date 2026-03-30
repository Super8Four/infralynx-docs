# Disaster Recovery Guide

The current InfraLynx disaster recovery baseline is designed for the bootstrap platform state, not yet for the final database-backed production topology.

## Recovery Priorities

1. restore authentication and RBAC access
2. restore inventory and validation-critical state
3. restore job, scheduler, and workflow state
4. restore audit and integration data

## Recommended Sequence

1. Assess whether the incident is isolated or full-environment.
2. Select the most recent known-good backup.
3. Run restore validation.
4. Restore the minimum required sections.
5. Run platform validation checks.
6. Confirm API read paths and administrative access.
7. Resume change activity only after validation passes.

## Known Limits

- backup persistence is still file-backed
- cross-engine database-native restore automation is documented, not yet active
- large audit or media datasets will need stronger retention and archival handling later
