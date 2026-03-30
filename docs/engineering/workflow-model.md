# Workflow Model

InfraLynx approval workflows are intentionally narrow in the current release. A workflow record represents an explicit approval request, not a generic business-process engine.

## Core Record

Each approval request stores:

- `id`
- `type`
- `title`
- `payload`
- `status`
- `requested_by`
- `assigned_to`
- `created_at`
- `updated_at`

## Assignment Model

Assignments are explicit and support both:

- direct user assignment
- role-based assignment

This keeps approval ownership visible even when the eventual approver is resolved through RBAC rather than a hard-coded username.

## Execution Binding

Requests may optionally contain an execution binding:

- `jobType`
- `payload`
- `triggeredJobId`

When present, approval does not execute work inline. Instead, the approved request enqueues a standard background job through the job engine.

## Scope

Workflow records can carry tenant, site, and device context so later enforcement can remain aligned to scoped RBAC rules rather than global-only decisions.
