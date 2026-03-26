# Authentication Model

InfraLynx authentication is modeled as an identity and session concern separate from authorization.

## Core Concepts

- identity: who the subject is
- authentication method: how the subject proved identity
- session: the issued runtime credential window
- tenant context: which tenant boundary the subject belongs to

## Supported Authentication Methods

- password
- SSO
- API token
- service account

## Design Direction

- authentication should produce a normalized identity object
- downstream services should consume identity plus tenant context, not provider-specific claims
- session issuance and expiration must stay explicit and auditable
- provider integrations will be adapters layered on top of this model later

## Exclusions in This Chunk

- no password storage implementation
- no token signing implementation
- no SSO provider integration
- no user-management UI
