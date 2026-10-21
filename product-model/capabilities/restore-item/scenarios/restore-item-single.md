---
kind: primary
routes:
  main: Main path
steps:
- text: The User clears a completed Item's checkbox.
  kind: actor
  entities:
  - entity: item
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product returns the Item to Active and clears its completion time.
  kind: product
  entities:
  - entity: item
    effect: changes
    from: Completed
    to: Active
    facts:
    - Completed at
    - Updated at
  actor: user
  contexts:
    main:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: src/lib/db/items.ts#restoreItem
- kind: code
  role: implementation
  target: src/components/items/ItemRow.tsx#ItemRow
- kind: code
  role: implementation
  target: src/components/views/BoardView/BoardView.tsx#BoardView
---

# Reopen a completed item

## Trigger

The User clears the checkbox of a completed item in the list or on the board.

## Outcome

The item is Active again, with no completion time.
