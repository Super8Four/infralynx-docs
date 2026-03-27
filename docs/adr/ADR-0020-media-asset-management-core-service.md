# ADR-0020: Media Asset Management Core Service

## Status

Accepted

## Context

InfraLynx needs image and file support across multiple domains, but none of the domain models should become the owner of file storage or media metadata. Media handling must stay independent from the UI layer and must be capable of moving from local storage to cloud-backed storage later.

## Decision

InfraLynx will implement media management as a standalone core service with:

- explicit media metadata records
- explicit media-link records
- local-first object storage behind a storage adapter boundary
- file-backed metadata persistence as the initial operational baseline
- tenant-aware RBAC enforcement on upload and retrieval

## Consequences

Domains can reference media through links without embedding file concerns. The current persistence approach is operational but temporary, so later chunks can replace local metadata storage and local object storage without breaking the contract shape.
