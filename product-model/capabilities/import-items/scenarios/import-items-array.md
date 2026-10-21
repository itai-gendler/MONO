---
kind: primary
routes:
  main: Main path
steps:
- text: The User chooses a JSON collection file.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::import-data
- text: The Product creates Items with the supplied title, notes, type, priority, and tags.
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

# Import fresh items

## Trigger

The User selects a valid JSON item collection whose entries are active.

## Outcome

Entries with a title become new items in the active workspace and the result reports how many were added.

## Edge cases

- Entries without a title are skipped.
