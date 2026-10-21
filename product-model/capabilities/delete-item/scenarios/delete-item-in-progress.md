---
kind: primary
routes:
  main: Main path
steps:
- text: The User chooses Delete for an Item.
  kind: actor
  entities:
  - entity: item
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    main:
      place: web::item-details
- text: The Product removes the Item and its Sub-items and Attachments.
  kind: product
  entities:
  - entity: item
    effect: removes
    from: In Progress
  - entity: sub-item
    effect: removes
    from: Incomplete
    with: item
  - entity: attachment
    effect: removes
    with: item
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

# Delete work in progress

## Trigger

The User deletes an in-progress item from Item Details.

## Outcome

The item and its checklist entries and attached files are permanently removed, and Item Details closes.
