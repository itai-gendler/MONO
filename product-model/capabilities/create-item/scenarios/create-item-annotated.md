---
kind: primary
routes:
  main: Main path
steps:
- text: The User submits an annotated title.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product extracts the supported annotations and creates the Item in the active context.
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

# Capture tags, urgency, and a date

## Trigger

The User submits “Prepare report #work !high @tomorrow”.

## Outcome

The task title is Prepare report, its tag is work, priority is High, and its due date is tomorrow.

## Edge cases

- An unrecognized date remains part of the title.
- Supported relative dates include today, tomorrow, next week, weekdays, and in a number of days or weeks.
