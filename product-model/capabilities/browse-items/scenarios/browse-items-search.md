---
kind: primary
routes:
  main: Main path
steps:
- text: The User enters a query.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::command-palette
- text: The Product searches item title, notes, content, and tags and returns matching items.
  kind: product
  entities:
  - entity: item
    effect: reads
    facts:
    - Title
    - Notes
    - Content
    - Tags
    - Updated at
  actor: user
  contexts:
    main:
      place: web::command-palette
references:
- kind: code
  role: implementation
  target: src/lib/db/items.ts#searchItems
---

# Search the workspace

## Trigger

The User types a query in the Command Palette.

## Outcome

Up to eight matching items are offered, most recently updated first, from every project of the active workspace.

## Edge cases

- A blank query supplies no item results.
- No matches or a failed local search leaves an empty item result list.
