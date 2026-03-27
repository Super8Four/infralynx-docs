# Authentication Security Considerations

## Mandatory Controls

- keep local admin enabled as a fallback
- encrypt provider secrets at rest
- validate provider configuration before enabling
- issue short-lived access tokens and longer-lived refresh tokens
- support logout and refresh explicitly
- log authentication events

## Bootstrap Constraints

The current implementation uses encrypted file-backed auth persistence. This is operational for bootstrap environments but is not the long-term production storage target.

## Consumer Expectations

- APIs must treat auth tokens as the source of user identity
- RBAC is evaluated after identity resolution
- downstream systems must not infer provider state from UI-only behavior

## Remaining Hardening

- external secret manager support
- stronger provider-specific validation depth
- broader session revocation and idle timeout policy
