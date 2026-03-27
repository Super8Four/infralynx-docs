# UI Data Flow

The InfraLynx UI data layer is structured to keep transport, normalization, state, and rendering responsibilities separate.

```mermaid
flowchart LR
  A["API /api/overview"] --> B["services/api-client"]
  B --> C["services/domain-overview"]
  C --> D["hooks/use-domain-overview"]
  D --> E["state/domain-overview-state"]
  E --> F["app.tsx shell rendering"]
```

## Flow Rules

- transport concerns stay in services
- normalization happens once per response
- hooks coordinate asynchronous loading and retry behavior
- reducer state defines loading, ready, and error transitions
- components render from normalized state only

## Benefits

- clearer failure boundaries
- lower coupling to backend schemas
- easier future expansion to caching, invalidation, and mutation workflows
