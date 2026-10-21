---
kind: primary
routes:
  main: Main path
steps:
- text: The User submits the named IF/THEN instruction.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::automations
- text: The Product creates the Automation Rule.
  kind: product
  entities:
  - entity: automation-rule
    effect: creates
    to: Enabled
    facts:
    - Name
    - Trigger
    - Action
    - Created at
  actor: user
  contexts:
    main:
      place: web::automations
references:
- kind: code
  role: implementation
  target: src/components/automation/AutomationModal.tsx#AutomationModal
- kind: code
  role: implementation
  target: src/lib/store/automationStore.ts#useAutomationStore
- kind: code
  role: implementation
  target: src/lib/automation/ruleEngine.ts#evaluateAutomations
---

# Save an enabled rule

## Trigger

The User supplies a rule name, condition type and value, and action type and value.

## Outcome

The new enabled rule is appended to the saved rule order.

## Edge cases

- Blank name, condition value, or action value prevents creation.
