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

The API surface now includes baseline read endpoints for shell-facing data, a standalone media API for upload and retrieval, a jobs API for asynchronous background execution, import/export APIs for structured transfer workflows, and a webhook/events API for outbound integration delivery. Documentation is still growing by subsystem, but the framework is now paired with active contracts.

## Documentation Rules

- Prefer contract-first descriptions over transport-specific implementation detail.
- Call out backward compatibility expectations explicitly.
- Reference ADRs for versioning or contract policy decisions.
