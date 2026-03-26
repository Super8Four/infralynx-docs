# ADR-0005: Establish the Platform Monorepo Foundation

- Status: Accepted
- Date: 2026-03-26

## Context

InfraLynx requires a scalable application repository structure that separates runtime concerns, shared libraries, tests, deployment-facing assets, and future database migration work before feature implementation begins.

## Decision

The `infralynx-platform` repository will begin as a Node.js and TypeScript workspace with separate application entry points for web, API, and worker runtimes, plus shared packages for configuration, domain contracts, and cross-cutting utilities.

## Consequences

- Teams gain clear ownership boundaries early.
- Shared code is explicit and reviewable through package boundaries.
- Future domain work can expand within a stable repo structure instead of reshaping the repository during feature delivery.
