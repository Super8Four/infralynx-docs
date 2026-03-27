# Topology UI Interaction Behavior

The first topology graph favors clarity and determinism over advanced canvas behavior.

## Supported Interactions

- click a node to select it
- inspect connected links in the side panel
- filter by site
- filter by device role
- optionally filter by VLAN
- zoom in and out
- reset the viewport
- pan the graph by dragging inside the canvas

## Interaction Rules

- node selection is single-select
- selection never infers hidden neighbors beyond the visible filtered graph
- filter changes preserve the current selection only if that node remains visible
- viewport changes do not alter the underlying graph model

## Operator Expectations

- the graph should feel stable between refreshes
- labels should remain readable without heavy decoration
- graph controls should remain functional on smaller viewports

## Deferred Behavior

The following are intentionally out of scope for the initial graph view:

- auto-layout recomputation from user drag actions
- edge routing around obstacles
- clustering or collapsing groups
- topology editing
