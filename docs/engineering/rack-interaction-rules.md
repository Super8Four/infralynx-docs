# Rack Interaction Rules

The rack elevation surface is interactive, but the behavior stays deliberately narrow and deterministic.

## Selection Rules

- clicking a device selects that device
- selecting a device defaults the inspector to its first port
- clicking a port selects that port without changing the rack layout
- the selected port drives the basic cable trace output

## Rendering Rules

- empty rack units remain visible to preserve spatial context
- selected devices receive a stronger visual treatment
- port status is expressed through consistent state coloring
- the rack stage remains visible inside the existing shell, not in a detached modal

## UX Rules

- U markers must remain readable while scrolling the rack
- device labels only render on the first occupied unit for that device
- loading and error states must not break navigation or the rest of the workspace
- interactions should work with simple buttons and not require drag-and-drop
