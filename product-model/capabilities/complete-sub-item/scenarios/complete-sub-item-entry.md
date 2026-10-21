---
kind: primary
routes:
  main: Main path
steps:
- text: The User ticks a checklist entry.
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
- text: The Product marks the Sub-item Completed.
  kind: product
  entities:
  - entity: sub-item
    effect: changes
    from: Incomplete
    to: Completed
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

# Complete one checklist entry

## Trigger

The User ticks an entry in an item’s checklist.

## Outcome

The entry is Completed and the checklist count and progress go up; the item itself keeps its status.
