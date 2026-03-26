# ADR-0002: Bootstrap the GitHub Operating System

- Status: Accepted
- Date: 2026-03-26

## Context

InfraLynx is structured as a multi-repository program. Consistent GitHub governance is required before collaborative implementation begins so that branching, review, issue intake, milestones, and ownership rules behave consistently across repositories.

## Decision

InfraLynx will define a reusable GitHub operating system in `infralynx-standards` that includes:

1. issue templates,
2. pull request templates,
3. CODEOWNERS,
4. label catalog,
5. milestone catalog,
6. project board structure,
7. branch protection policy,
8. repository default settings,
9. contributor, security, support, and changelog policies.

These artifacts are authored centrally and will be rolled out to each program repository in later chunks.

## Consequences

- Governance becomes reviewable and versioned like any other engineering asset.
- Repository bootstrap work is faster and more consistent.
- Some controls remain declarative until GitHub repositories and automations are provisioned.
