# Page Hierarchy Rules

InfraLynx page hierarchy must stay explicit, shallow, and durable across domains.

## Hierarchy model

- breadcrumb trails are defined from route metadata, not inferred from URL fragments
- top-level hierarchy should map to platform areas or domains
- secondary hierarchy should describe the current working surface, not a visual widget

## Rules

- every top-level route must declare its hierarchy path
- hierarchy labels must be stable operational nouns
- reserved future domains must keep their place in the navigation model even before feature completion
- cross-domain surfaces must map back to a single owning route for navigation purposes

## Current hierarchy baseline

- Workspace / Overview
- Domains / Core Platform
- Domains / IPAM
- Domains / DCIM
- Domains / Networking
- Domains / Virtualization
- Services / Automation

## Anti-patterns

- deriving breadcrumbs from component nesting
- letting feature screens invent parallel navigation trees
- encoding hierarchy only in color or icon treatment
