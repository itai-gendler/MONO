---
kind: primary
result: achieved
routes:
  main: Web
steps:
- text: The User picks an icon and enters a name.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspaces
  capability: create-workspace
- text: The Product creates the Workspace and makes it active.
  kind: product
  entities:
  - entity: workspace
    effect: creates
    facts:
    - Name
    - Icon
    - Order
    - Created at
    - Updated at
  actor: user
  contexts:
    main:
      place: web::workspace
  capability: create-workspace
- text: The User captures the first task.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
  capability: create-item
- text: The Product creates the Item in the new Workspace.
  kind: product
  entities:
  - entity: item
    effect: creates
    to: Active
    facts:
    - Title
    - Notes
    - Content
    - Type
    - Priority
    - Due date
    - Tags
    - Properties
    - Placement
    - Order
    - Pinned
    - Completed at
    - Created at
    - Updated at
  - entity: workspace
    effect: reads
    facts: []
  actor: user
  contexts:
    main:
      place: web::workspace
  capability: create-item
references:
- kind: code
  role: implementation
  target: src/app/app/page.tsx#CreateWorkspaceModal
- kind: code
  role: implementation
  target: src/lib/db/workspaces.ts#createWorkspace
- kind: code
  role: implementation
  target: src/components/items/QuickCapture.tsx#QuickCapture
- kind: code
  role: implementation
  target: src/lib/db/items.ts#createItem
---

# Create a workspace and capture its first task

## Trigger

The User chooses a first-run template or New Workspace.

## Outcome

The workspace is active, and the task captured next is saved in it.
