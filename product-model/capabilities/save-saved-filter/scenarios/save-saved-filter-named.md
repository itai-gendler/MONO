---
kind: primary
routes:
  main: Main path
steps:
- text: The User names the filter.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product creates a Saved Filter from the current criteria.
  kind: product
  entities:
  - entity: saved-filter
    effect: creates
    facts:
    - Name
    - Criteria
    - Created at
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

# Save active criteria

## Trigger

The User chooses Save Filter for active criteria and supplies a name.

## Outcome

A named filter is retained across reloads.

## Edge cases

- A cancelled naming prompt or whitespace-only name saves nothing.
