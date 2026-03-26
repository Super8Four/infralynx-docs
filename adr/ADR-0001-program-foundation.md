# ADR-0001: Establish InfraLynx Program Foundation

- Status: Accepted
- Date: 2026-03-26

## Context

InfraLynx is a greenfield enterprise infrastructure platform intended to replace NetBox while supporting multiple SQL engines, strict Git collaboration, and a modular domain architecture. The program requires a stable foundation before application features begin.

## Decision

InfraLynx will begin as a coordinated multi-repository program with separate repositories for platform code, documentation, infrastructure, standards, and design.

Program execution will proceed in small, reviewable chunks. No major feature implementation will begin until:

1. repository roles are defined,
2. documentation scaffolding exists,
3. governance artifacts are specified,
4. CI/CD phases are planned,
5. an ADR process is active.

## Consequences

- Governance and documentation are treated as first-class deliverables.
- Architectural changes will require ADRs from the start.
- Platform implementation is intentionally delayed until standards and workflows are in place.
- Multi-repository coordination overhead is accepted in exchange for clearer ownership and long-term maintainability.
