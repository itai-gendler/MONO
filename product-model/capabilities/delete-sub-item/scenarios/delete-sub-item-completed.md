---
kind: primary
routes:
  main: Main path
steps:
- text: The User deletes a completed checklist entry.
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
- text: The Product removes the Sub-item.
  kind: product
  entities:
  - entity: sub-item
    effect: removes
    from: Completed
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

# Remove a completed checklist entry

## Trigger

The User deletes a ticked entry from an item’s checklist.

## Outcome

The entry is gone, and the checklist count and progress reflect the remaining entries.
