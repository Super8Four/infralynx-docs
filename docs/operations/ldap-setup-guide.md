# LDAP Setup Guide

Use LDAP primarily for Active Directory-backed username and password authentication.

## Minimum Inputs

- LDAP host
- TCP port
- bind DN
- bind password
- search base
- SSL setting

## Recommended Pattern

- use `ldaps://` where possible
- scope the bind account to search-only privileges
- keep the search base narrow enough to avoid expensive directory scans
- align usernames to `userPrincipalName`, `mail`, or `sAMAccountName`

## Validation

Use the `Test Connection` action in the provider UI before enabling the provider.

Expected checks:

- service bind succeeds
- server is reachable
- search base is usable

## Failure Modes

- invalid bind credentials
- unreachable server or blocked TLS
- search base that does not contain the intended users
