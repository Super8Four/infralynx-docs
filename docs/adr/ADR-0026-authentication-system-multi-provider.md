# ADR-0026: Multi-Provider Authentication System

- Title: Multi-Provider Authentication System
- Status: Accepted

## Context

InfraLynx needed a real authentication system rather than the earlier bootstrap header-based identity shortcut. The platform also needed simultaneous support for local recovery access, LDAP-backed enterprise login, OIDC for Azure AD, and SAML for environments that still require it.

## Decision

InfraLynx will use a provider-based authentication architecture.

- `@infralynx/auth-core` owns provider records, session records, encrypted config handling, and token issuance.
- Each provider library is wrapped in an isolated adapter package.
- OIDC uses `openid-client`.
- LDAP uses `ldapts`.
- SAML uses `@node-saml/node-saml`.
- Sessions use signed JWT access and refresh tokens.
- Provider configuration is managed through the UI and exposed through the auth API.
- Local admin access remains permanently available as a fallback.

## Consequences

Positive:

- provider logic stays contained
- enterprise auth can be added without touching domain models
- the UI config model matches the operational runtime model

Negative:

- bootstrap persistence is still file-backed until the database-backed auth persistence slice lands
- session and secret management still need deeper production hardening later
