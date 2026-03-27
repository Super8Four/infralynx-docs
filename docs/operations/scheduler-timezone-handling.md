# Scheduler Timezone Handling

The bootstrap scheduler stores schedules centrally but executes them in `UTC` only.

## Why

UTC-only scheduling removes ambiguity while the platform is still establishing its core job and event model.

## Current Behavior

- API accepts `timezone`
- scheduler validates and currently permits `UTC` only
- `next_run` is computed from UTC timestamps
- worker comparisons are performed against UTC ISO timestamps

## Future Expansion

Later work should introduce:

- named IANA timezone support
- daylight-saving-safe next-run calculation
- schedule preview and drift diagnostics
