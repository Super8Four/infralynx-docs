# ADR-0012: Cross-Domain Integration Model

- Title: Cross-Domain Integration Model
- Status: Accepted

## Context

InfraLynx now has separate core, IPAM, DCIM, and UI domain packages. Cross-domain relationships are required to connect those domains, but embedding foreign objects inside each domain package would create tight coupling and unclear ownership.

## Decision

InfraLynx will:

- introduce `@infralynx/network-domain` for cross-domain binding contracts
- keep relationships explicit and ID-based
- update `ipam-domain` and `dcim-domain` only where relationship identifiers are naturally owned by those entities
- keep validation helpers in the integration layer so runtime services can reuse one consistent contract model

## Consequences

- domain ownership stays clear while relationships remain first-class
- cross-domain validation is testable before full integration services exist
- package coupling remains controlled because objects are not embedded across domains
- later networking and topology work can build on the explicit binding layer instead of inventing hidden joins
