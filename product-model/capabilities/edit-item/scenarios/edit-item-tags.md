---
kind: primary
routes:
  main: Main path
steps:
- text: The User edits the selected Item.
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
- text: The Product saves the Item tags.
  kind: product
  entities:
  - entity: item
    effect: changes
    facts:
    - Tags
    - Updated at
  actor: user
  contexts:
    main:
      place: web::item-details
references:
- kind: code
  role: implementation
  target: src/components/items/ItemDetailPanel.tsx#ItemDetailPanel
- kind: code
  role: implementation
  target: src/components/ui/MarkdownEditor.tsx#MarkdownEditor
- kind: code
  role: implementation
  target: src/lib/db/items.ts#updateItem
---

# Edit item tags

## Trigger

The User adds or removes a label.

## Outcome

Added tags are trimmed and lowercase; an exact duplicate is ignored. Removing a tag removes that value from this item.
