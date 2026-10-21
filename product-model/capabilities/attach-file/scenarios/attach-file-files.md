---
kind: primary
routes:
  main: Main path
steps:
- text: The User selects local files.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::item-details
- text: The Product creates each Attachment and retains its contents with the selected item.
  kind: product
  entities:
  - entity: attachment
    effect: creates
    facts:
    - Name
    - Media type
    - Size
    - Contents
    - Added at
  - entity: item
    effect: reads
    facts: []
  actor: user
  contexts:
    main:
      place: web::item-details
references:
- kind: code
  role: implementation
  target: src/components/items/AttachmentManager.tsx#AttachmentManager
- kind: code
  role: implementation
  target: src/lib/db/items.ts#updateItem
---

# Attach local files

## Trigger

The User selects one or more files.

## Outcome

The files are kept with the item and images can be previewed locally.
