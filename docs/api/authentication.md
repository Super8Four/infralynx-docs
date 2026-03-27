# Authentication API

## Provider Management

- `GET /api/auth/providers`
- `POST /api/auth/providers`
- `GET /api/auth/providers/{id}`
- `PUT /api/auth/providers/{id}`
- `DELETE /api/auth/providers/{id}`
- `POST /api/auth/providers/{id}/test`
- `GET /api/auth/providers/enabled`

## Login Flows

- `POST /api/auth/login/local`
- `POST /api/auth/login/ldap`
- `POST /api/auth/login/oidc/start`
- `GET /api/auth/oidc/callback`
- `POST /api/auth/login/saml/start`
- `POST /api/auth/saml/callback`

## Session Management

- `GET /api/auth/session`
- `POST /api/auth/refresh`
- `POST /api/auth/logout`

## Notes

- local and LDAP return session tokens directly
- OIDC and SAML complete through callback redirects back into the UI
- provider config responses return masked secret fields rather than raw secrets
