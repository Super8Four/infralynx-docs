# Cross-Domain Validation Rules

The first integration layer validates relationship shape without creating runtime coupling.

## Rules

- interface-to-IP bindings must reference distinct binding, IP, and prefix IDs
- access VLAN bindings must be untagged
- trunk VLAN bindings must be tagged
- cable bindings must reference two distinct interfaces
- prefix hierarchy bindings must not self-reference
- interface bindings must remain ID-based and never embed full DCIM or IPAM records

## Coupling Controls

- cross-domain validation belongs in `@infralynx/network-domain`
- DCIM and IPAM packages should only expose fields they own directly
- runtime services can compose these contracts later, but they must not redefine them

## Test Scenarios

- valid interface-to-IP binding in a single VRF
- invalid access VLAN binding marked as tagged
- invalid cable binding that loops back to the same interface
- invalid prefix hierarchy self-reference
- valid interface to VLAN and cable bindings across two devices
