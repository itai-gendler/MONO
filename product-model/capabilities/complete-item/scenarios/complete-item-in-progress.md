---
kind: primary
routes:
  main: Main path
steps:
- text: The User ticks an In Progress card's checkbox.
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
- text: The Product completes the Item.
  kind: product
  entities:
  - entity: item
    effect: changes
    from: In Progress
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

# Complete work in progress

## Trigger

The User ticks an In Progress card on the board.

## Outcome

The item is Completed with its completion time recorded.
