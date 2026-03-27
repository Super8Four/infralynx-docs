# IPAM Visualization Behavior

The initial IPAM tree is designed as a dense operational view rather than a diagram.

## Supported Behavior

- group prefixes by VRF
- expand and collapse VRF sections
- expand and collapse nested prefixes
- select a prefix for detail inspection
- show utilization bars for each visible prefix

## Interaction Rules

- root VRF groups are expanded by default
- root prefixes are expanded by default
- deeper branches expand on demand
- selection is single-select
- utilization display remains stable during expansion changes

## UI Goals

- preserve readability under moderate depth
- expose utilization without needing a separate report
- avoid recursive rendering work during every interaction by using pre-flattened rows
