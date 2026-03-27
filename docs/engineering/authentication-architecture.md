# Authentication Architecture

InfraLynx authentication is provider-based and centrally managed.

## Goals

- support local, LDAP, OIDC, and SAML simultaneously
- keep provider-specific logic isolated from the rest of the platform
- preserve local admin fallback access
- enforce RBAC after identity resolution
- keep provider secrets encrypted at rest

## Service Layout

- `@infralynx/auth-core`
  owns provider records, encrypted config storage, user mappings, session records, JWT issuance, refresh, logout, and auth logs
- `@infralynx/auth-providers/local`
  owns local username and password verification
- `@infralynx/auth-providers/ldap`
  owns LDAP connection testing, directory search, and credential verification
- `@infralynx/auth-providers/oidc`
  owns OIDC discovery, authorization redirect generation, and authorization-code callback completion
- `@infralynx/auth-providers/saml`
  owns SAML metadata parsing, redirect generation, and ACS response validation
- `apps/api/src/auth`
  exposes the operational auth API and keeps the rest of the API boundary provider-agnostic

## Persistence Model

The target relational model is:

- `auth_provider`
  `id`, `name`, `type`, `enabled`, `config`, `is_default`, `created_at`
- `user_provider_mapping`
  `user_id`, `provider_id`, `external_id`
- `auth_session`
  `id`, `user_id`, `provider_id`, `subject`, `tenant_id`, `role_ids`, `access_expires_at`, `refresh_expires_at`
- `auth_log`
  `id`, `level`, `action`, `actor_id`, `provider_id`, `session_id`, `message`, `created_at`

The current bootstrap implementation persists the same shapes in encrypted file-backed state so the platform can run before the database-backed auth persistence slice lands.

## Request Flow

1. User opens login.
2. UI loads enabled providers from `/api/auth/providers/enabled`.
3. User either submits credentials or is redirected to OIDC or SAML.
4. Auth API resolves provider-specific identity.
5. Identity is mapped to an InfraLynx user or created through controlled mapping behavior.
6. Session tokens are issued.
7. Downstream APIs authorize actions using resolved role IDs.
