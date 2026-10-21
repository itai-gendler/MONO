---
kind: primary
routes:
  main: Main path
steps:
- text: The User clears a completed checklist entry.
  kind: actor
  entities:
  - entity: sub-item
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    main:
      place: web::item-details
- text: The Product returns the Sub-item to Incomplete.
  kind: product
  entities:
  - entity: sub-item
    effect: changes
    from: Completed
    to: Incomplete
    facts:
    - Updated at
  actor: user
  contexts:
    main:
      place: web::item-details
references:
- kind: code
  role: implementation
  target: src/components/items/ChecklistManager.tsx#ChecklistManager
- kind: code
  role: implementation
  target: src/components/items/ItemDetailPanel.tsx#ItemDetailPanel
- kind: code
  role: implementation
  target: src/lib/db/items.ts
---

# Reopen one checklist entry

## Trigger

The User clears a ticked entry in an item’s checklist.

## Outcome

The entry is Incomplete again and the checklist count and progress go down; the item itself keeps its status.
