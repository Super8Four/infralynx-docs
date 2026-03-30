# Workflow Use Cases

The first workflow foundation is meant for controlled operational actions, not broad process automation.

## Primary Use Cases

- approval before executing a sensitive background job
- change-control sign-off for infrastructure actions
- access-review acknowledgement with an auditable decision trail

## Current Fit

Use approval workflows when InfraLynx needs:

- explicit ownership
- clear pending versus decided state
- RBAC-aware reviewer targeting
- a durable record before execution

## Current Non-Goals

The current implementation is not intended to provide:

- BPMN-style orchestration
- multi-step branching logic
- SLA timers
- escalation chains
- parallel approval stages

Those would add complexity too early and are intentionally deferred.
