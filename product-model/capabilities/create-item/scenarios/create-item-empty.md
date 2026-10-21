---
kind: validation
routes:
  main: Main path
steps:
- text: The User submits an empty title.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The parsed title is empty; capture remains available.
  kind: condition
  entities: []
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

# Do not save an empty capture

## Trigger

The capture is blank or contains only recognized annotations.

## Outcome

No new item is created.
