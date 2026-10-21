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
  target: src/components/views/BoardView/BoardCard.tsx#BoardCard
- kind: code
  role: implementation
  target: src/components/views/BoardView/BoardView.tsx#BoardView
---

# Finish a card in progress

## Trigger

The User moves an In Progress card to Completed.

## Outcome

The item is Completed and its completion time is recorded.
