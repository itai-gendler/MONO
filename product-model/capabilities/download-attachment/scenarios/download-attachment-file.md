---
kind: primary
routes:
  main: Main path
steps:
- text: The User selects an Attachment.
  kind: actor
  entities:
  - entity: attachment
    effect: reads
    facts:
    - Name
    - Contents
  actor: user
  contexts:
    main:
      place: web::item-details
- text: The Product delivers the Attachment contents as a file.
  kind: product
  entities:
  - entity: attachment
    effect: reads
    facts:
    - Name
    - Contents
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

# Download the original file

## Trigger

The User selects an attachment’s download action.

## Outcome

A download uses the original name and locally stored contents.
