---
kind: primary
routes:
  main: Main path
steps:
- text: The User supplies search criteria.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product matches item title, notes, content, and tags case-insensitively and combines the text match with status and priority.
  kind: product
  entities:
  - entity: item
    effect: reads
    facts:
    - Title
    - Notes
    - Content
    - Tags
    - Priority
  actor: user
  contexts:
    main:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: src/components/views/SearchView/SmartFilterBar.tsx#SmartFilterBar
---

# Combine item filters

## Trigger

The User types search text and picks a status and a priority in the filter bar.

## Outcome

Only items matching every chosen criterion remain: the text in their title, notes, content or tags, ignoring case, and the chosen status and priority. Reset clears all criteria.
