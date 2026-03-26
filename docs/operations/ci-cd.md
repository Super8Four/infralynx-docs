# CI/CD Overview

InfraLynx CI/CD starts with a fast validation baseline and expands in phases as the platform grows.

## Pipeline Explanation

The initial GitHub Actions baseline has two workflows:

- `PR Validation` for pull requests targeting `main` or `develop`
- `Build` for direct branch builds on `main` and `develop`

## PR Validation Stages

- lint
- typecheck
- build
- test
- dependency scan

## Contribution CI Expectations

- pull requests are expected to pass all validation jobs before merge
- contributors should run relevant checks locally before opening or updating a PR
- dependency issues at or above the configured severity threshold should be fixed or explicitly addressed before merge

## Expansion Path

Later chunks will extend CI into:

- artifact generation
- multi-database testing
- container validation
- staged delivery workflows
