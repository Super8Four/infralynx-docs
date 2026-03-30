# Audit Event Types

InfraLynx audit actions use stable dotted names.

## Current Categories

- `auth.login.*`
- `auth.provider.*`
- `auth.session.*`
- `inventory.record.*`
- `job.*`
- `webhook.*`
- `rbac.*`

## Naming Rules

- use domain-first names
- keep verbs explicit
- avoid UI-specific wording
- keep the action stable even if the implementation changes
