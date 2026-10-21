---
kind: primary
result: achieved
routes:
  main: Web
steps:
- text: The User selects an Item in the list.
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
  capability: open-item
- text: The Product opens Item Details with the Item, its checklist and its files.
  kind: product
  entities:
  - entity: item
    effect: reads
    facts:
    - Title
    - Notes
  actor: user
  contexts:
    main:
      place: web::item-details
  capability: open-item
- text: The User writes in Notes & Markdown.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::item-details
  capability: edit-item
- text: The Product saves the Item notes when the User leaves the editor.
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
  capability: edit-item
references:
- kind: code
  role: implementation
  target: src/components/items/ItemRow.tsx#ItemRow
- kind: code
  role: implementation
  target: src/components/items/ItemDetailPanel.tsx#ItemDetailPanel
- kind: code
  role: implementation
  target: src/components/ui/MarkdownEditor.tsx#MarkdownEditor
---

# Open a task and write its notes

## Trigger

The User selects a task in the list.

## Outcome

The task's notes are saved and stay with the task in Item Details.
