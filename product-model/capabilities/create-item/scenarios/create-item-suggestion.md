---
kind: primary
routes:
  main: Main path
steps:
- text: The User chooses a suggested tag or priority and submits the capture.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product creates the Item from the resulting input.
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

# Use a local capture suggestion

## Trigger

The typed text produces a suggested tag or priority.

## Outcome

The chosen suggestion is added to the capture input; the submitted task contains it.
