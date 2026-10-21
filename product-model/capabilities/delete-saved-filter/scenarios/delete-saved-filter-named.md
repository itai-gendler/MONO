---
kind: primary
routes:
  main: Main path
steps:
- text: The User selects a Saved Filter for removal.
  kind: actor
  entities:
  - entity: saved-filter
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product removes the Saved Filter.
  kind: product
  entities:
  - entity: saved-filter
    effect: removes
  actor: user
  contexts:
    main:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: src/lib/store/appStore.ts#useAppStore
- kind: code
  role: implementation
  target: src/components/views/SearchView/SmartFilterBar.tsx#SmartFilterBar
- kind: code
  role: implementation
  target: src/components/layout/Sidebar.tsx#Sidebar
---

# Delete a saved filter

## Trigger

The User removes a named filter.

## Outcome

The saved entry disappears without deleting matching items.
