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
- text: The Product saves the supplied Item attributes without replacing other facts.
  kind: product
  entities:
  - entity: item
    effect: changes
    facts:
    - Title
    - Priority
    - Due date
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

# Edit title, date, and priority

## Trigger

The User edits an item’s title, due date, or priority.

## Outcome

The same item reflects the new attributes; clearing the date removes its schedule.
