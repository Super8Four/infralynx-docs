# ADR-0019: Global Navigation Refinement

## Status

Accepted

## Context

The initial UI shell established a three-region application frame, but navigation semantics were still too loose for long-term domain expansion. InfraLynx needs a consistent route model spanning core platform, IPAM, DCIM, networking, virtualization, and automation without forcing each page to define its own layout behavior.

## Decision

InfraLynx will use a shared navigation contract in `@infralynx/ui` that defines:

- grouped sidebar navigation
- explicit breadcrumb hierarchy
- route-owned quick actions
- route-owned context links
- stable domain-to-route mappings

The web application will render a persistent left sidebar, a top bar for page identity and actions, and a right context rail for hierarchy and local references.

## Consequences

Navigation becomes more predictable and scalable across domains, and route behavior is centralized instead of spreading through page components. The tradeoff is that future domains must integrate with the shared route model rather than inventing local navigation patterns.
