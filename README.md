# InfraLynx Documentation

[![Docs Build](https://github.com/Super8Four/infralynx-docs/actions/workflows/docs-build.yml/badge.svg?style=flat-square)](https://github.com/Super8Four/infralynx-docs/actions/workflows/docs-build.yml)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg?style=flat-square)](LICENSE)
[![Version](https://img.shields.io/badge/version-v0.12.0--alpha%2Bchunk31.1-E6E1D9?style=flat-square&labelColor=2A3F5F)](VERSION)
[![Node.js](https://img.shields.io/badge/Node.js-24-5FA04E?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-supported-336791?style=flat-square&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![MS%20SQL%20Server](https://img.shields.io/badge/MS%20SQL%20Server-supported-CC2927?style=flat-square&logo=microsoftsqlserver&logoColor=white)](https://www.microsoft.com/sql-server/)
[![MariaDB](https://img.shields.io/badge/MariaDB-supported-003545?style=flat-square&logo=mariadb&logoColor=white)](https://mariadb.org/)
[![Documentation](https://img.shields.io/badge/docs-MkDocs-526CFE?style=flat-square&logo=materialformkdocs&logoColor=white)](https://super8four.github.io/infralynx-docs/)

Official documentation, standards, architecture, and deployment guides for InfraLynx.

Quick Links: [Documentation Site](https://super8four.github.io/infralynx-docs/) | [Platform Repo](https://github.com/Super8Four/infralynx-platform) | [Docs Repo](https://github.com/Super8Four/infralynx-docs) | [Standards Repo](https://github.com/Super8Four/infralynx-standards) | [Design Repo](https://github.com/Super8Four/infralynx-design) | [Infra Repo](https://github.com/Super8Four/infralynx-infra)

## Overview

`infralynx-docs` is the canonical written source for InfraLynx architecture, operations, API contracts, governance, release notes, legal position, and contributor onboarding. It explains how the platform works and how the rest of the repository ecosystem fits together.

## Current Status

- Repository version: `v0.12.0-alpha+chunk31.1`
- Program snapshot: `v0.1.0-alpha+chunk31`
- Current chunk: `31.1`
- Current phase: `Scale / Reliability`
- Next milestone: `Chunk 32 -> API Versioning`
- Target release: `v1.0.0`

The docs repo tracks the active platform build and is maintained as a first-class product artifact, not a secondary export.

## Roadmap Progress

Completed:
- Core platform
- IPAM
- DCIM
- Operations
- Security
- Performance

In Progress:
- Reliability / API hardening

Upcoming:
- Product differentiators
- Visual subnet planning
- Network containers
- AI integrations

## Tech Stack

- Markdown and MkDocs Material
- GitHub Pages publishing
- InfraLynx architecture, API, and operations source material
- Cross-repo governance and ADR documentation

## Getting Started

1. Install MkDocs dependencies in your environment.
2. From this repo, build the site:

```powershell
python -m mkdocs build --strict
```

3. Serve locally if needed:

```powershell
python -m mkdocs serve
```

## Documentation Links

- [Published Site](https://super8four.github.io/infralynx-docs/)
- [Repository Map](https://super8four.github.io/infralynx-docs/engineering/platform-repository/)
- [Onboarding Guide](https://super8four.github.io/infralynx-docs/development/onboarding/)
- [Versioning Strategy](https://super8four.github.io/infralynx-docs/development/versioning/)
- [Contributing Guide](CONTRIBUTING.md)

## InfraLynx Repository Ecosystem

- [infralynx-platform](https://github.com/Super8Four/infralynx-platform): runtime application code and shared packages
- [infralynx-docs](https://github.com/Super8Four/infralynx-docs): official written reference for the platform
- [infralynx-infra](https://github.com/Super8Four/infralynx-infra): infrastructure-as-code and deployment configuration
- [infralynx-standards](https://github.com/Super8Four/infralynx-standards): governance and contributor standards
- [infralynx-design](https://github.com/Super8Four/infralynx-design): design system direction and visual assets

## Contribution Guidelines

Documentation changes should land with the behavior or policy changes they describe whenever possible. Use [CONTRIBUTING.md](CONTRIBUTING.md) and the standards repo as the operating baseline.

## Support InfraLynx

Support continued development of InfraLynx:

[https://buymeacoffee.com/infralynx](https://buymeacoffee.com/infralynx)

Support helps fund:
- New features
- Documentation
- Hosted services
- Enterprise integrations

## License

This repository is licensed under Apache 2.0. See [LICENSE](LICENSE) and [NOTICE](NOTICE).

## Support / Community

- [Published Docs](https://super8four.github.io/infralynx-docs/)
- [Support Policy](SUPPORT.md)
- [Security Policy](SECURITY.md)
- [Code of Conduct](CODE_OF_CONDUCT.md)
