# SAML Setup Guide

SAML is the enterprise fallback for environments that cannot use OIDC.

## Required Inputs

- metadata URL or metadata XML
- SP entity ID
- ACS URL

## What InfraLynx Uses From Metadata

- IdP SSO entry point
- IdP signing certificate

## ACS Recommendation

Use the API callback endpoint:

- `http://localhost:4010/api/auth/saml/callback` for local bootstrap environments

## Operational Notes

- metadata should be preferred over manual certificate entry
- consumers must expect assertion-driven login, not username/password collection
- local admin access should remain enabled while the SAML path is being validated
