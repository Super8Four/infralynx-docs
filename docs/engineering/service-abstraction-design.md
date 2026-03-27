# Service Abstraction Design

InfraLynx wraps external libraries behind internal service boundaries so infrastructure dependencies do not leak into domain logic.

## Design Rules

- Domain packages define business contracts and validation rules.
- Infrastructure packages own library integration details.
- API and worker runtimes depend on InfraLynx abstractions, not directly on vendor APIs where avoidable.
- External configuration stays in InfraLynx records and service inputs rather than hard-coded library setup files.

## Standardized Boundaries

- `@infralynx/auth-core` and `@infralynx/auth-providers/*`
  Library-backed auth providers with shared provider records and session flows.
- `@infralynx/job-core` and `@infralynx/job-queue`
  BullMQ-backed queue execution with InfraLynx job metadata and logs.
- `@infralynx/scheduler`
  Schedule persistence plus cron-backed trigger orchestration.
- `@infralynx/webhooks`
  Event matching, signing, delivery records, and axios-backed outbound delivery.
- `@infralynx/media-core` and `@infralynx/media-storage`
  Metadata, linking, validation, upload parsing, and storage adapters.
- `@infralynx/ui` with `@infralynx/network-domain`
  Stable topology view contracts with React Flow only in the rendering layer.

## Anti-Patterns

- embedding library types in domain records
- passing raw vendor clients through domain services
- storing provider config in environment files when the product requires UI management
- making UI components responsible for infrastructure protocol behavior
