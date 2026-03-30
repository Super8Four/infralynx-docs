# ADR-0030: Approval Workflows Foundation

- Status: Accepted
- Date: 2026-03-30

## Context

InfraLynx needs a controlled way to gate sensitive actions without introducing a full orchestration engine. The platform already has RBAC, jobs, and audit logging, so approvals should build on those primitives instead of bypassing them.

## Decision

InfraLynx will implement a small approval-workflow foundation that:

- stores explicit approval request records
- supports `pending`, `approved`, and `rejected` states
- assigns review responsibility to users and roles
- enforces review decisions through the API
- enqueues standard jobs after approval when execution is required

## Consequences

Positive:

- approval ownership is explicit
- execution remains centralized in the job engine
- RBAC and audit logging stay first-class

Negative:

- the first release does not support multi-stage approvals
- rejection and approval are terminal
- escalation behavior is deferred
