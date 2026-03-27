# Rack Rendering Model

Chunk 14 introduces the first reusable rack elevation model for InfraLynx.

## Core Rules

- rack devices are positioned by explicit starting U and height
- rendering order is deterministic from highest U to lowest U
- rack occupancy is derived from reusable slot generation helpers
- device blocks span multiple units visually without duplicating device metadata

## Ownership

- API payloads provide rack, device, port, and cable data
- `@infralynx/ui` owns slot generation and rack geometry helpers
- `apps/web` owns the React rendering and selection behavior

## Visual Model

- each rack unit is rendered as a grid row
- devices visually occupy all units they span
- the starting unit renders the main device label and metadata
- continuation units preserve occupancy without repeating the full label block

## Cable Model

Cable visualization is intentionally lightweight in this chunk.

- ports expose peer labels and cable IDs
- the selected port renders a simple source-to-destination cable trace
- full topology visualization remains a later chunk
