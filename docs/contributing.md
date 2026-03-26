# Contribution Guide

InfraLynx documentation is a maintained product artifact, not a secondary output. Contributions should improve clarity, accuracy, and long-term maintainability.

## Contribution Rules

- Keep changes scoped and reviewable.
- Update documentation in the same change as the behavior or policy change when possible.
- Add an ADR when architecture or governance changes.
- Preserve audience separation between product, engineering, operations, API, release, and design content.

## Documentation Review Expectations

- Validate links, navigation placement, and terminology consistency.
- Prefer direct language over speculative or marketing-heavy phrasing.
- Avoid duplicating architectural decisions outside ADRs.

## CI Expectations

- Open pull requests with a buildable and reviewable state.
- Expect lint, typecheck, build, test, and dependency scan checks to run in GitHub Actions.
- Treat failing CI as a merge blocker unless an explicit exception is documented and approved.

## ADR Usage

Use the ADR template for new decisions that affect architecture, deployment, governance, interfaces, or long-term contributor constraints.
