# UI Interaction Patterns

InfraLynx Phase 1 uses a single interaction model across core CRUD surfaces:

- persistent left navigation
- route-aware top bar
- table list view
- detail page
- create and edit forms
- explicit delete confirmation

## Interaction Rules

- Navigation changes route context, not component state only.
- List rows are selectable and open detail views.
- Create and edit forms always submit through the API layer.
- Delete actions must require confirmation before mutation.
- Empty, loading, and error states must remain distinct.

## Phase 1 Surface Pattern

Each writable resource follows the same sequence:

1. list
2. create
3. detail
4. edit
5. delete

This keeps operator movement predictable while the product surface is still growing.

## Relationship Display

Relationship sections are required on detail views when related data exists:

- device detail shows interfaces, IP addresses, and connections
- rack detail shows resident devices
- site detail shows racks and devices
- prefix detail shows child prefixes and IP allocations
- IP address detail shows prefix, VRF, interface, and device context
