# Performance Thresholds

Chunk 31 establishes bootstrap pass and fail thresholds for the current control-plane runtime.

## Thresholds

| Scenario | Success Rate | p95 Target | Notes |
| --- | --- | --- | --- |
| API concurrency | 99% | 900 ms | Read-heavy baseline across overview, search, inventory, and cache |
| Concurrent sessions | 99% | 1000 ms | Login, refresh, and authenticated session read |
| Job enqueue saturation | 98% | 1400 ms | Queue-write and list-read pressure against the jobs API |

## Usage

- `smoke` profile: quick validation for developer and CI use
- `baseline` profile: fuller local validation before larger releases or infrastructure changes

## Interpretation

- a failed success-rate threshold is treated as a correctness or saturation problem, not just a latency regression
- a failed p95 threshold indicates the request path is no longer stable at the expected concurrency level
- p99 is tracked in Artillery configs as an early warning signal even when only p95 is used as the formal gate
