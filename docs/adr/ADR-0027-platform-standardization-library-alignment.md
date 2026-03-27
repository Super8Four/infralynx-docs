# ADR-0027: Platform Standardization Library Alignment

- Status: Accepted
- Date: 2026-03-27

## Context

InfraLynx had accumulated several custom infrastructure implementations for concerns that are already solved well by established libraries. That increased maintenance cost and created avoidable operational risk.

## Decision

InfraLynx will standardize on wrapped third-party libraries for non-core infrastructure concerns:

- `openid-client` for OIDC
- `ldapjs` for LDAP
- `passport-saml` for SAML
- `bcrypt` for password hashing
- `bullmq` for async job execution
- `node-cron` for recurring schedule triggers
- `axios` for outbound webhook delivery
- `multer` for upload parsing
- `reactflow` for topology graph rendering

These libraries must stay behind InfraLynx-owned abstractions so domain logic, records, and UI contracts remain stable.

## Consequences

- The platform reduces custom infrastructure code and aligns with production-grade libraries.
- Some selected libraries introduce lifecycle risk of their own and may need future replacement, especially where upstream maintenance is weak.
- InfraLynx retains portability because application code depends on internal abstractions rather than direct vendor APIs.
