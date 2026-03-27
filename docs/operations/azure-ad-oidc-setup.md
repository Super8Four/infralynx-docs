# Azure AD / OIDC Setup

Azure AD is the primary enterprise authentication path for InfraLynx.

## Required Registration Data

- client ID
- client secret
- issuer URL
- redirect URI

## Recommended Redirect

Use the API callback endpoint:

- `http://localhost:4010/api/auth/oidc/callback` for local bootstrap environments

Production environments should use the externally reachable API origin.

## Flow

1. InfraLynx performs OIDC discovery.
2. UI requests an authorization redirect.
3. User authenticates with the identity provider.
4. Callback exchanges the authorization code using PKCE.
5. InfraLynx maps the returned subject to a platform user.

## Notes

- PKCE is always used
- issuer configuration must match the Azure tenant and app registration
- client secrets are encrypted at rest inside the auth service
