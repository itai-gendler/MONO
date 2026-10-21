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
- text: The Product saves the Item notes after editing finishes.
  kind: product
  entities:
  - entity: item
    effect: changes
    facts:
    - Notes
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

# Save notes on any item

## Trigger

The User edits the Notes & Markdown content.

## Outcome

Trimmed notes are retained; an empty note clears the existing notes.
