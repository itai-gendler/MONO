---
kind: primary
routes:
  main: Main path
steps:
- text: The User chooses an Attachment.
  kind: actor
  entities:
  - entity: attachment
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    main:
      place: web::item-details
- text: The Product removes the Attachment.
  kind: product
  entities:
  - entity: attachment
    effect: removes
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

# Remove an attachment

## Trigger

The User selects Delete for an attachment.

## Outcome

The item retains its other files and no longer includes this attachment.
