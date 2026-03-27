# Versioning Strategy

InfraLynx uses Semantic Versioning for all public releases:

- `MAJOR` for breaking changes
- `MINOR` for backward-compatible feature additions
- `PATCH` for backward-compatible fixes

## Current Baseline

The current baseline is `v0.3.0-alpha`.

## Pre-release Tags

- `alpha` for active foundation and integration work
- `beta` for feature-complete stabilization
- `rc` for release candidates that are expected to become the next stable release unless blocking issues are found

## Build Metadata

InfraLynx may append optional internal metadata for progress tracking, for example:

- `v0.3.0-alpha+chunk22.5`
- `v0.3.0-alpha+chunk23`

This metadata does not change version precedence. It is used for internal build identification, chunk tracking, and release coordination.

## Version Progression

- Move from `alpha` to `beta` after the core platform surface is coherent and end-to-end usable.
- Move from `beta` to `rc` when the release scope is locked and compatibility verification is underway.
- Cut `v1.0.0` only after the API, domain boundaries, UI, and operational workflows are stable enough to support compatibility commitments.

## Release Expectations

- Every release should update `VERSION` and `CHANGELOG.md`.
- Repository READMEs should reference the current public version.
- ADRs should reflect meaningful versioning or compatibility decisions.

## Compatibility Rules

- Breaking API or contract changes require a major version increment.
- New optional capabilities that do not break existing integrations require a minor version increment.
- Corrections that preserve behavior and compatibility require a patch version increment.
