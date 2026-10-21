---
kind: validation
routes:
  main: Main path
steps:
- text: The User clears the title.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::item-details
- text: A nonblank title is required for saving.
  kind: condition
  entities: []
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

# Keep the saved title when input is blank

## Trigger

The User leaves the title empty.

## Outcome

No blank title is persisted.
