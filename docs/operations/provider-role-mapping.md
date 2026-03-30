# Provider Role Mapping

InfraLynx supports mapping external identity signals into internal roles.

## Supported Inputs

- LDAP groups
- OIDC claims
- SAML attributes

## Mapping Rules

- mappings are stored centrally
- mappings target a single InfraLynx role
- mappings can be global, tenant-scoped, site-scoped, or device-scoped
- a user can receive multiple mapped assignments from one provider

## Operational Guidance

- always preserve local admin fallback
- validate provider config before enabling a mapping-driven provider
- keep mapping inputs stable and explicit
- prefer tenant-level mappings before site or device specialization
