---
kind: primary
routes:
  main: Main path
steps:
- text: The User selects a Saved Filter.
  kind: actor
  entities:
  - entity: saved-filter
    effect: reads
    facts:
    - Name
    - Criteria
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product filters items with the saved criteria.
  kind: product
  entities:
  - entity: saved-filter
    effect: reads
    facts:
    - Criteria
  - entity: item
    effect: reads
    facts:
    - Title
    - Notes
    - Content
    - Priority
    - Tags
    - Pinned
  actor: user
  contexts:
    main:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: src/components/layout/Sidebar.tsx#Sidebar
- kind: code
  role: implementation
  target: src/lib/store/appStore.ts#useAppStore
---

# Apply a saved filter

## Trigger

The User selects a saved filter in the sidebar.

## Outcome

The saved criteria become the active filter, and the view shows only the items that match them.
