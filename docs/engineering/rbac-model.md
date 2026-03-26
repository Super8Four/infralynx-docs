# RBAC Model

InfraLynx uses RBAC to keep authorization predictable across product domains.

## Model

- permission: action allowed on a resource
- role: named bundle of permissions
- assignment: roles granted to an authenticated identity
- access decision: allow or deny result for a requested permission

## Early Baseline

The current skeleton defines:

- permission identifiers like `tenant:read`
- role identifiers like `platform-admin`
- authorization evaluation based on assigned role IDs

## Design Rules

- roles must remain business-readable
- permissions must stay stable and machine-oriented
- application code should ask for a permission decision, not inspect role names directly
- domain-specific permissions will extend the core set later rather than replacing it

## Risks to Control

- role explosion from overly specific roles
- permission names tied too tightly to UI screens
- hidden authorization logic outside shared policy evaluation
