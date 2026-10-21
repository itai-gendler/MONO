---
kind: edge
routes:
  main: Main path
steps:
- text: The User submits a task while offline.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product creates the Item in local storage.
  kind: product
  entities:
  - entity: item
    effect: creates
    to: Active
    facts:
    - Title
    - Notes
    - Content
    - Type
    - Priority
    - Due date
    - Tags
    - Properties
    - Placement
    - Order
    - Pinned
    - Completed at
    - Created at
    - Updated at
  actor: user
  contexts:
    main:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: src/components/items/QuickCapture.tsx#QuickCapture
- kind: code
  role: implementation
  target: src/components/items/QuickCapture.tsx#parseQuickInput
- kind: code
  role: implementation
  target: src/lib/db/items.ts#createItem
- kind: code
  role: implementation
  target: src/lib/utils/date.ts#parseNaturalDate
- kind: code
  role: implementation
  target: src/lib/automation/ruleEngine.ts#evaluateAutomations
---

# Capture while offline

## Trigger

The app is already available locally and connectivity is absent.

## Outcome

The task is saved on the device and visible without waiting for a server.
