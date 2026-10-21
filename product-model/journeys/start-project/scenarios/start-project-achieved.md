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
      place: web::new-project
  capability: create-project
- text: The Product creates the Project and selects it.
  kind: product
  entities:
  - entity: project
    effect: creates
    facts:
    - Name
    - Icon
    - Order
    - Created at
    - Updated at
  - entity: workspace
    effect: reads
    facts: []
  actor: user
  contexts:
    main:
      place: web::workspace
  capability: create-project
- text: The User captures the first task.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
  capability: create-item
- text: The Product creates the Item in the new Project.
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
  - entity: project
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
  target: src/components/layout/CreateProjectModal.tsx#CreateProjectModal
- kind: code
  role: implementation
  target: src/lib/db/workspaces.ts#createProject
- kind: code
  role: implementation
  target: src/components/items/QuickCapture.tsx#QuickCapture
- kind: code
  role: implementation
  target: src/lib/db/items.ts#createItem
---

# Create a project and capture its first task

## Trigger

The User chooses to create a project in the active workspace.

## Outcome

The project is selected, and the task captured next is saved in it.
