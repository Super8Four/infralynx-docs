# RBAC Model

InfraLynx uses RBAC to keep authorization predictable across product domains.

## Core Terms

- permission: action allowed on a resource
- role: named bundle of permissions
- assignment: a role granted at a specific scope
- provider mapping: external group or claim translated into an assignment
- access decision: allow or deny result for a requested permission and scope

## Current Model

The current RBAC layer defines:

- permission identifiers like `device:write`
- scope-aware assignments for `global`, `tenant`, `site`, and `device`
- provider role mappings for LDAP, OIDC, and SAML inputs
- authorization evaluation based on effective grants, not only raw role IDs

## Design Rules

- roles must remain business-readable
- permissions must stay stable and machine-oriented
- application code should ask for a permission decision, not inspect role names directly
- provider-specific values must be normalized before they influence authorization

## Risks to Control

- role explosion from overly specific roles
- scope misuse causing inconsistent access
- hidden authorization logic outside shared policy evaluation
