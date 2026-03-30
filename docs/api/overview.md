# API Documentation Overview

InfraLynx API documentation is intended to describe contracts, integration expectations, versioning, authentication, and domain-specific resource behavior.

## API Documentation Structure

API documentation should be organized by:

- authentication and authorization model
- versioning and compatibility policy
- resource families by domain
- integration examples and constraints
- operational concerns such as rate limits, auditing, and webhooks

## Current Status

The InfraLynx API now treats `/api/v1` as the stable integration namespace. Legacy `/api/*` routes remain temporarily available for compatibility, but they are marked as deprecated and documented under the formal deprecation policy.

The API surface includes baseline read endpoints for shell-facing data, media upload and retrieval, jobs, scheduler definitions, backup workflows, cache visibility, import and export operations, validation, workflows, audit access, and webhook or event integration delivery.

## Versioning Baseline

- Use `/api/v1/*` for all new integrations.
- Expect standardized JSON metadata on versioned responses.
- Expect standardized error envelopes on versioned failures.
- Treat legacy `/api/*` routes as compatibility-only paths pending retirement.

## Documentation Rules

- Prefer contract-first descriptions over transport-specific implementation detail.
- Call out backward compatibility expectations explicitly.
- Reference ADRs for versioning or contract policy decisions.
