# Approval Lifecycle

The current approval lifecycle is intentionally simple:

1. `pending`
2. `approved`
3. `rejected`

## Pending

Requests begin in `pending`. Only assigned users or users holding assigned roles can review them.

## Approved

Approval records who approved the request, when it happened, and any optional comment. If the request includes an execution binding, approval also enqueues the associated background job.

## Rejected

Rejection stores the reviewer, timestamp, and optional comment. Rejected requests are terminal in the current implementation.

## Enforcement Rules

- reviews are API-enforced, not UI-only
- tenant boundaries are checked before review
- non-pending requests cannot be reviewed again
- execution happens only after approval
