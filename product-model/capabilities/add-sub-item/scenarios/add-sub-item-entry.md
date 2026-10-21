---
kind: primary
routes:
  main: Main path
steps:
- text: The User supplies a checklist entry title.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::item-details
- text: The Product creates the Sub-item at the next checklist position.
  kind: product
  entities:
  - entity: sub-item
    effect: creates
    to: Incomplete
    facts:
    - Title
    - Order
    - Created at
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

# Add a checklist entry

## Trigger

The User enters a nonblank checklist title.

## Outcome

The new entry is incomplete and follows existing entries.

## Edge cases

- Blank or whitespace-only titles cannot be submitted.
