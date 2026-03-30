# Scaling Recommendations

Chunk 31 does not claim final production sizing. It establishes a repository-owned baseline and identifies where future scaling work should focus.

## Current recommendations

- treat the current runtime as a bootstrap control plane, not final enterprise throughput capacity
- scale API and worker processes independently because read traffic and queue pressure fail differently
- keep Redis external and durable for cache and queue coordination before increasing worker concurrency
- move high-write subsystems off file-backed state before attempting aggressive horizontal scaling

## Near-term priorities

- add live Redis-backed queue and cache load runs in environments that match expected deployment topology
- add engine-specific database connection pool validation for PostgreSQL, MSSQL, and MariaDB
- profile worker saturation under real queued execution rather than enqueue-only pressure
- capture trend baselines over time instead of relying on single-run point measurements

## Expected bottlenecks in the current stage

- file-backed inventory and auth state under concurrent writes
- job enqueue pressure before worker throughput becomes the dominant limit
- session issuance churn when many users authenticate at once
