---
kind: primary
routes:
  main: Main path
steps:
- text: The User deletes a checklist entry.
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
    from: Incomplete
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

# Remove a checklist entry

## Trigger

The User chooses Delete for an open entry.

## Outcome

The checklist no longer contains that entry; the item and its other entries stay.
