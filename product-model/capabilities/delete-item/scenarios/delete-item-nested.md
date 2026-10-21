---
kind: primary
routes:
  main: Main path
steps:
- text: The User chooses the parent for deletion.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::item-details
- text: The Product removes the parent Item, child Items, and their Sub-items.
  kind: product
  entities:
  - entity: item
    effect: removes
    as: parent
    from: Active
  - entity: item
    effect: removes
    as: child
    from: Active
    with: parent
  - entity: sub-item
    effect: removes
    from: Completed
    with: child
  actor: user
  contexts:
    main:
      place: web::item-details
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

# Delete a restored item tree

## Trigger

A restored backup contains a parent item and nested children.

## Outcome

Deleting the parent recursively removes descendants and their checklists.
