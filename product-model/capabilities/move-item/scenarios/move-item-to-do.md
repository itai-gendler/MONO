---
kind: primary
routes:
  main: Main path
steps:
- text: The User drags the Item to another column, or picks the column under Move to.
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
- text: The Product changes the Item status.
  kind: product
  entities:
  - entity: item
    effect: changes
    from: In Progress
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
  target: src/components/views/BoardView/BoardCard.tsx#BoardCard
- kind: code
  role: implementation
  target: src/components/views/BoardView/BoardView.tsx#BoardView
---

# Move a card back to To Do

## Trigger

The User moves an In Progress card back to To Do.

## Outcome

The item is Active again and shows under To Do.
