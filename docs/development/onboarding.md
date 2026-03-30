# Contributor Onboarding

This guide explains how to approach InfraLynx as a contributor without guessing where things live.

## Start Here

1. Read the repository README for the repo you are entering.
2. Review the standards repository for contribution and governance expectations.
3. Use this docs repository to understand architecture, APIs, operations, and ADR history.
4. Make changes in the repository that owns the concern rather than adding cross-cutting drift.

## Repository Selection

- Use `infralynx-platform` for runtime code, APIs, workers, UI, migrations, and tests.
- Use `infralynx-docs` for architecture, release, operations, and API documentation.
- Use `infralynx-infra` for deployment, hosting, and infrastructure-as-code.
- Use `infralynx-standards` for governance, templates, and contributor policy.
- Use `infralynx-design` for design-system direction, UX guidance, and shared assets.

## Working Expectations

- Keep changes scoped.
- Update docs with behavior or policy changes.
- Add or update ADRs when architectural decisions change.
- Preserve InfraLynx service abstractions and avoid leaking library-specific logic outside infrastructure layers.
- Treat lint, typecheck, test, build, and docs validation as the normal merge baseline.

## Program Snapshot

- Program snapshot: `v0.1.0-alpha+chunk31`
- Current phase: `Scale / Reliability`
- Next milestone: `Chunk 32 -> API Versioning`
- Target release: `v1.0.0`

## Helpful Links

- [Repository Map](../engineering/platform-repository.md)
- [Versioning Strategy](versioning.md)
- [Contributing Guide](../contributing.md)
