---
kind: primary
routes:
  main: Main path
steps:
- text: The User ticks an active Item's checkbox.
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
- text: The Product marks the Item Completed and records its completion time.
  kind: product
  entities:
  - entity: item
    effect: changes
    from: Active
    to: Completed
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
  target: src/lib/db/items.ts#completeItem
- kind: code
  role: implementation
  target: src/components/items/ItemRow.tsx#ItemRow
- kind: code
  role: implementation
  target: src/components/views/BoardView/BoardView.tsx#BoardView
---

# Complete an item

## Trigger

The User ticks an active item in the list or on the board.

## Outcome

The item is Completed and its completion time is recorded.
