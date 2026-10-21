---
kind: primary
routes:
  main: Main path
steps:
- text: The User reads Automation Rules.
  kind: actor
  entities:
  - entity: automation-rule
    effect: reads
    facts:
    - Name
    - Trigger
    - Action
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

# Inspect saved rules

## Trigger

The User opens Visual Automations.

## Outcome

Saved rules show their names, condition, action, and whether enabled.

## Edge cases

- An empty rule list offers rule creation.
