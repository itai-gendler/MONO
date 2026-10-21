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
- text: The Product saves the Item properties.
  kind: product
  entities:
  - entity: item
    effect: changes
    facts:
    - Properties
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

# Edit custom values

## Trigger

The User supplies a custom property name and value, or removes one.

## Outcome

Nonblank names and values are trimmed; an existing name’s value is replaced. Removing a property leaves the others intact.
