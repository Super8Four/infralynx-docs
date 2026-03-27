# External Library Usage Policy

InfraLynx uses external libraries for solved infrastructure problems and keeps custom code focused on domain modeling, orchestration, and product behavior.

## Policy Rules

- Use established libraries for authentication protocols, queues, scheduling, HTTP delivery, upload parsing, and graph rendering.
- Keep all library usage behind InfraLynx-owned service layers or adapters.
- Do not import infrastructure libraries directly into domain packages unless the package is the abstraction boundary for that concern.
- Prefer replaceable wrappers over vendor-specific coupling in application code.

## Current Standardized Libraries

- OIDC: `openid-client`
- LDAP: `ldapjs`
- SAML: `@node-saml/node-saml` as the maintained equivalent to older `passport-saml` guidance
- Password hashing: `bcrypt`
- Jobs: `bullmq`
- Scheduling: `node-cron`
- Webhook HTTP delivery: `axios`
- Media upload parsing: `multer`
- Topology graph rendering: `reactflow`

## Replacement Boundary

External libraries may change over time. The stable contract for the rest of the platform is:

- provider abstractions in `packages/auth-providers/*`
- queue abstractions in `packages/job-queue`
- schedule abstractions in `packages/scheduler`
- delivery abstractions in `packages/webhooks`
- upload and storage abstractions in `packages/media-*`
- rendering contracts in `packages/ui` plus `packages/network-domain`

That boundary keeps domain logic stable even when infrastructure dependencies change.
