# Changelog

All notable changes to this repository will be documented in this file.

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
