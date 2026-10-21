---
kind: primary
routes:
  main: Main path
steps:
- text: The User opens Inbox or selects a workspace.
  kind: actor
  entities:
  - entity: workspace
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product reads the workspace's top-level Items in their order.
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
    - Order
  - entity: workspace
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

# Read the workspace's list

## Trigger

The User opens Inbox, or selects a workspace, with the List view chosen.

## Outcome

Every top-level item of the workspace is listed, whichever project it belongs to. Completed items are left out while Show completed is off.

## Edge cases

- A workspace with no items shows the empty list.
