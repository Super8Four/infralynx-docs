# Navigation Structure

InfraLynx navigation is organized as a stable operational shell rather than a page-by-page menu.

## Primary layout

- left sidebar for persistent primary navigation
- top bar for page identity, breadcrumbs, and quick actions
- main workspace for task execution and visualization
- right context rail for hierarchy cues, local actions, and operational notes

## Group model

Navigation is grouped to keep expansion predictable:

- Platform for overview and workspace-wide entry points
- Domains for core, IPAM, DCIM, networking, and virtualization
- Services for automation and future service surfaces

## Route rules

- each route has a stable ID
- each route owns a label, summary, accent, and hierarchy trail
- each route maps to a data-domain identifier or a reserved placeholder
- each route declares quick actions and context links explicitly

## Navigation ownership

Shared navigation contracts live in `@infralynx/ui` so the shell can stay consistent as more views are added. The web app consumes those contracts and renders them, but does not define route hierarchy ad hoc in individual screens.
