# IPAM Nesting Validation Requirements

InfraLynx validates hierarchy consistency before IPAM tree data reaches the browser.

## Validation Requirements

- parent prefix must exist
- parent and child VRF IDs must match
- child prefix length must be greater than parent prefix length
- hierarchy traversal must not encounter a cycle
- all prefixes in the tree must have parseable CIDRs

## Utilization Requirements

- utilization is computed per prefix after hierarchy construction
- direct IP assignments count toward prefix consumption
- child prefix capacity contributes to parent utilization when capacity can be estimated
- large prefixes may report capacity as pending instead of fabricating a value

## Failure Handling

If hierarchy validation fails, InfraLynx should block rendering of that invalid branch rather than infer a corrected structure.
