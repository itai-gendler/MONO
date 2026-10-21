---
kind: validation
routes:
  main: Main path
steps:
- text: The User chooses an invalid file.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::import-data
- text: The Product reports the import error.
  kind: product
  entities: []
  actor: user
  contexts:
    main:
      place: web::import-data
references:
- kind: code
  role: implementation
  target: src/components/ImportExport/ImportDialog.tsx#ImportDialog
- kind: code
  role: implementation
  target: src/lib/db/items.ts#createItem
---

# Report an invalid import

## Trigger

The chosen file has the wrong extension, invalid JSON, or no item collection.

## Outcome

The User sees a format or parse error and can choose another file.
