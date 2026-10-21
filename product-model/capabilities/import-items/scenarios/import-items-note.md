---
kind: primary
routes:
  main: Main path
steps:
- text: The User chooses a JSON collection containing an active note.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::import-data
- text: The Product creates an Item with note type and the supplied notes, title, priority, and tags.
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
      place: web::import-data
references:
- kind: code
  role: implementation
  target: src/components/ImportExport/ImportDialog.tsx#ImportDialog
- kind: code
  role: implementation
  target: src/lib/db/items.ts#createItem
---

# Import a note into the shared item collection

## Trigger

The User imports an active note with title, notes, priority, and tags.

## Outcome

The imported note is a new item in the active workspace. Its notes can be read and edited through the same Item Details process as a task.
