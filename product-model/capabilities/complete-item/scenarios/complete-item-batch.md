---
kind: primary
routes:
  main: Main path
steps:
- text: The User selects several Items and chooses Complete.
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
- text: The Product completes the selected Items.
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

# Complete selected items

## Trigger

The User selects several active items and chooses Complete.

## Outcome

Each selected item is Completed with its completion time, and the selection is cleared.

## Edge cases

- If saving fails partway, the failure is reported; items already completed stay completed.
