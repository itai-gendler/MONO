---
kind: primary
routes:
  main: Main path
steps:
- text: The User chooses Delete for selected items.
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
- text: The Product removes each selected Item.
  kind: product
  entities:
  - entity: item
    effect: removes
    from: Completed
  actor: user
  contexts:
    main:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: src/lib/db/items.ts#deleteItem
- kind: code
  role: implementation
  target: src/components/items/ItemDetailPanel.tsx#ItemDetailPanel
- kind: code
  role: implementation
  target: src/components/layout/BatchActionBar.tsx#BatchActionBar
---

# Delete selected items

## Trigger

The User chooses Delete for a selection.

## Outcome

Selected items are removed and the selection is cleared.

## Edge cases

- A failed delete is reported; earlier successful deletions remain.
