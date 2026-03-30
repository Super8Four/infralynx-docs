# TTL Standards

InfraLynx uses short, explicit TTLs for API cache entries.

## Current Defaults

- overview: 30 seconds
- search: 30 seconds
- inventory navigation: 45 seconds
- inventory lists: 45 seconds
- inventory details: 60 seconds
- topology, rack, and IPAM demo views: 45 seconds
- enabled auth providers: 60 seconds
- auth provider list and detail: 45 seconds
- auth session status: 20 seconds
- cached bearer identity resolution: 20 seconds
- RBAC summary: 20 seconds
- RBAC admin snapshot: 30 seconds

## Guidance

- use shorter TTLs for permission-sensitive or session-sensitive data
- use moderate TTLs for shared navigation and lookup data
- keep mutable operational data below 60 seconds unless invalidation is extremely reliable
- prefer explicit invalidation over long TTLs
