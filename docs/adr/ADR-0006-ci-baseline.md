# ADR-0006: Establish the Initial CI Baseline

- Status: Accepted
- Date: 2026-03-26

## Context

InfraLynx needs an initial CI baseline that validates repository health early, fails quickly on common errors, and can expand into more advanced delivery pipelines over time.

## Decision

InfraLynx will begin with GitHub Actions workflows that enforce pull request validation for linting, type checking, build verification, test execution, and dependency auditing. A separate branch build workflow will run on `main` and `develop`.

## Consequences

- Contributors receive fast feedback on common failures before merge.
- CI structure is ready to expand into artifact generation and environment promotion in later chunks.
- Branch protection can rely on concrete validation jobs instead of informal review alone.
