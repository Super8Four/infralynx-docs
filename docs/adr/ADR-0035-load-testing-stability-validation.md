# ADR-0035: Load Testing And Stability Validation

## Status

Accepted

## Context

InfraLynx had performance-sensitive control-plane features, but no repository-owned framework for concurrency testing or repeatable stability validation. The project needed a practical way to exercise the API, session handling, and job engine using a proven external tool rather than custom scripts.

## Decision

InfraLynx adopts Artillery as the standard load-testing framework for the current platform stage.

The repository will:

- keep scenario definitions under `tests/load`
- store shared thresholds and scenario metadata in `@infralynx/performance-tests`
- run smoke and baseline profiles through a dedicated Node runner
- document explicit thresholds and current bootstrap limitations

## Consequences

Positive:

- load validation becomes part of the normal repository workflow
- concurrency regressions can be detected earlier
- test definitions stay explicit and readable

Negative:

- current baselines still reflect a bootstrap runtime rather than final production topology
- live database pool validation remains incomplete until persistent engine adapters are in place
