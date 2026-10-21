---
kind: primary
routes:
  main: Main path
steps:
- text: The User selects a project in the sidebar.
  kind: actor
  entities:
  - entity: project
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product reads the selected Project's top-level Items.
  kind: product
  entities:
  - entity: item
    effect: reads
    facts:
    - Title
    - Notes
    - Priority
    - Due date
    - Tags
    - Placement
  - entity: project
    effect: reads
    facts: []
  actor: user
  contexts:
    main:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: src/components/layout/Sidebar.tsx#Sidebar
---

# Read a project

## Trigger

The User selects one of the workspace’s projects.

## Outcome

Only the project's top-level items are listed, and new captures go into that project.

## Edge cases

- A project with no items shows the empty list.
