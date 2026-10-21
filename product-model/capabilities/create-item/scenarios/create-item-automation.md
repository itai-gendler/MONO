---
kind: primary
routes:
  main: Main path
steps:
- text: 'The User captures “Call the supplier #urgent”.'
  kind: actor
  entities: []
  actor: user
  contexts: &id001
    main:
      place: web::workspace
- text: The Product creates the Item as an Active task tagged urgent.
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
  contexts: *id001
- text: The Product reads the enabled Automation Rules in their saved order.
  kind: product
  entities:
  - entity: automation-rule
    effect: reads
    facts:
    - Name
    - Trigger
    - Action
  actor: user
  contexts: *id001
- text: The first rule, Has Tag urgent then Set Priority high, sets the Item priority to High.
  kind: product
  entities:
  - entity: item
    effect: changes
    facts:
    - Priority
    - Updated at
  actor: user
  contexts: *id001
- text: The second rule, Priority equals high then Set Due Date today, sees the new priority and sets the Item due date to today.
  kind: product
  entities:
  - entity: item
    effect: changes
    facts:
    - Due date
    - Updated at
  actor: user
  contexts: *id001
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

# Capture with chained rules

## Trigger

Two rules are enabled in this order in Visual Automations: Has Tag urgent → Set Priority high, then Priority equals high → Set Due Date today. The User captures a task tagged urgent.

## Outcome

The task is saved with priority High and due today. The second rule matched only because the first one had already changed the priority.

## Decision points

### Rule evaluation

Does the current task match the next enabled rule?

- Matches → apply its action before evaluating the following rule.
- Does not match → continue without changing the task.

### Due-date action

Can the requested date be parsed?

- Yes → use the parsed date.
- No → keep the existing date.
