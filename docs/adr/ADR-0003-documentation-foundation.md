# ADR-0003: Establish MkDocs Documentation Foundation

- Status: Accepted
- Date: 2026-03-26

## Context

InfraLynx requires a documentation system that is version-aware, easy to maintain, suitable for enterprise program growth, and aligned with the product's dark-first design direction.

## Decision

InfraLynx documentation will use MkDocs with the Material theme as the primary documentation system. The site will adopt a dark navy branding layer through custom CSS and will organize content by audience and operational concern.

## Consequences

- Documentation gains a maintainable static site foundation with structured navigation and CI-friendly builds.
- Branding remains customizable without replacing the upstream theme.
- Contributors must maintain both content and site configuration as part of documentation work.
