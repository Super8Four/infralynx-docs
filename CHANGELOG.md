# Changelog

All notable changes to this repository will be documented in this file.

## [v0.10.0-alpha]

### Added
- Indexing strategy, query standards, DB engine performance notes, and ADR-0034 documentation.

### Changed
- Updated the documentation release baseline to `v0.10.0-alpha`.
- Expanded architecture and operations guidance to cover deterministic pagination, explain-plan validation, and cross-engine index planning.

### Fixed
- Clarified how InfraLynx performance tuning is staged before the persistent database adapters land.

### Removed
- None.

## [v0.9.0-alpha]

### Added
- Caching architecture, invalidation rules, TTL standards, cache API, and ADR-0033 documentation.

### Changed
- Updated the documentation release baseline to `v0.9.0-alpha`.
- Expanded performance guidance to cover Redis-backed API caching, scoped cache keys, and write-owned invalidation.

### Fixed
- Clarified how InfraLynx improves repeated read performance without leaking cache behavior into domain logic.

### Removed
- None.

## [v0.8.0-alpha]

### Added
- Backup strategy, restore procedure, disaster recovery, backup API, and ADR-0032 documentation.

### Changed
- Updated the documentation release baseline to `v0.8.0-alpha`.
- Expanded operations guidance to cover backup scheduling, restore validation, and rollback-aware recovery flows.

### Fixed
- Clarified how InfraLynx protects and restores the current file-backed runtime state while documenting the future DB-native strategy.

### Removed
- None.

## [v0.7.0-alpha]

### Added
- Validation rules, conflict detection logic, validation API, and ADR-0031 documentation.

### Changed
- Updated the documentation release baseline to `v0.7.0-alpha`.
- Expanded platform guidance to cover dry-run validation, write-path enforcement, and approval-workflow validation gates.

### Fixed
- Clarified how InfraLynx prevents overlapping IPAM records and broken DCIM relationships before data is committed.

### Removed
- None.

## [v0.6.0-alpha]

### Added
- Workflow model, approval lifecycle, use case, workflow API, and ADR-0030 documentation.

### Changed
- Updated the documentation release baseline to `v0.6.0-alpha`.
- Expanded platform guidance to cover approval-gated execution and role-based workflow review.

### Fixed
- Clarified how approval requests integrate with RBAC and the job engine instead of adding a separate execution subsystem.

### Removed
- None.

## [v0.5.0-alpha]

### Added
- Audit model, audit event type, audit query pattern, audit API, and ADR-0029 documentation.

### Changed
- Updated the documentation release baseline to `v0.5.0-alpha`.
- Extended operations guidance to include centralized audit usage and filtering patterns.

### Fixed
- Clarified the difference between local subsystem logs and the shared structured audit trail.

### Removed
- None.

## [v0.4.0-alpha]

### Added
- RBAC architecture, permission hierarchy, provider-role mapping, RBAC API, and ADR-0028 documentation.

### Changed
- Updated the documentation release baseline to `v0.4.0-alpha`.
- Expanded the RBAC guidance from a baseline model into scoped, provider-aware enforcement.

### Fixed
- Clarified that RBAC is enforced at the API layer and surfaced to the UI through permission summaries.

### Removed
- None.

## [v0.3.0-alpha]

### Added
- External library usage policy, service abstraction design guidance, dependency alignment documentation, and ADR-0027 for platform standardization.

### Changed
- Updated the documentation release baseline to `v0.3.0-alpha`.
- Extended architecture guidance to reflect BullMQ, node-cron, axios, multer, React Flow, and the standardized auth-provider library set.

### Fixed
- Clarified that infrastructure concerns must be wrapped behind InfraLynx-owned service layers instead of leaking library details into domain logic.

### Removed
- None.

## [v0.2.0-alpha]

### Added
- Authentication architecture, provider configuration, LDAP, Azure AD OIDC, SAML, security, and auth API documentation.
- ADR-0026 for the multi-provider authentication system and UI-managed provider strategy.

### Changed
- Updated the documentation release baseline to `v0.2.0-alpha`.
- Extended versioning guidance examples to reflect the current chunk milestone.

### Fixed
- None.

### Removed
- None.

## [v0.1.0-alpha]

### Added
- Initial InfraLynx product, engineering, operations, API, ADR, legal, and development documentation foundation.

### Changed
- Established Semantic Versioning with optional internal build metadata such as `v0.1.0-alpha+chunk21`.

### Fixed
- None.

### Removed
- Private commercial license placeholder.
