# Load Test Scenarios

InfraLynx uses Artillery as the standard framework for repeatable load and stability validation.

The repository-owned baseline scenarios are:

- `api-concurrency`: exercises the hot read surface across overview, search, inventory, and cache status endpoints
- `concurrent-sessions`: creates and refreshes local sessions while checking authenticated status reads
- `job-engine-stress`: applies concurrent write pressure to the jobs API to expose queueing bottlenecks

Scenario design rules:

- use explicit API contracts rather than private module hooks
- keep actor identity headers stable for deterministic authorization behavior
- validate concurrency on realistic platform workflows instead of isolated ping endpoints
- keep smoke and baseline profiles separate so CI can run a smaller gate while operators still have a richer local suite

Current baseline limitation:

- database connection pool testing is documented and staged, but live engine-specific pool validation remains a later step until the platform uses persistent engine adapters instead of bootstrap file-backed state
