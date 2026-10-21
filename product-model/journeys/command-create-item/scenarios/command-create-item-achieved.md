---
kind: primary
result: achieved
routes:
  main: Web
steps:
- text: The User picks the capture command in the Command Palette.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::command-palette
  capability: browse-commands
- text: The Product closes the palette and focuses Quick Capture.
  kind: product
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
  capability: browse-commands
- text: The User types the task and submits it.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
  capability: create-item
- text: The Product creates the Item as an Active task.
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
  actor: user
  contexts:
    main:
      place: web::workspace
  capability: create-item
references:
- kind: code
  role: implementation
  target: src/components/layout/CommandPalette.tsx#useCommandItems
- kind: code
  role: implementation
  target: src/components/items/QuickCapture.tsx#QuickCapture
- kind: code
  role: implementation
  target: src/lib/db/items.ts#createItem
---

# Capture a task from the Command Palette

## Trigger

The User opens the Command Palette and chooses New Item.

## Outcome

The task is saved as Active in the active workspace or project, and Quick Capture is clear for the next one.
