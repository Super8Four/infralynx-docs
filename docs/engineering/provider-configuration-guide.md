# Provider Configuration Guide

Provider setup is UI-managed under `Admin -> Authentication`.

## Local

Required fields:

- minimum password length

Use case:

- emergency fallback
- bootstrap administration
- recovery when enterprise identity is unavailable

## LDAP

Required fields:

- server
- port
- bind DN
- bind password
- search base
- SSL toggle

Behavior:

- InfraLynx binds with the service account
- searches for the requested user
- re-binds as the found directory user to validate credentials

## OIDC

Required fields:

- client ID
- client secret
- issuer URL
- redirect URI

Behavior:

- InfraLynx performs discovery dynamically
- uses authorization code flow with PKCE
- resolves identity from ID token and userinfo

## SAML

Required fields:

- metadata URL or metadata XML
- entity ID
- ACS URL

Behavior:

- InfraLynx extracts SSO URL and signing certificate from metadata
- generates the SP redirect
- validates the posted assertion at the ACS endpoint

## Operational Rules

- only one provider should be marked default
- local provider should remain enabled for fallback access
- test connection before enabling enterprise providers
- replace masked secret fields only when values actually change
