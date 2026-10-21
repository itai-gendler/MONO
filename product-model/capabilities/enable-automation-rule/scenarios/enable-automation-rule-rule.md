---
kind: primary
routes:
  main: Main path
steps:
- text: The User switches a disabled Automation Rule on.
  kind: actor
  entities:
  - entity: automation-rule
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    main:
      place: web::automations
- text: The Product enables the Automation Rule.
  kind: product
  entities:
  - entity: automation-rule
    effect: changes
    from: Disabled
    to: Enabled
    facts: []
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

# Enable a saved rule

## Trigger

The User switches on a disabled rule in Visual Automations.

## Outcome

The rule is enabled and applies to the next captures it matches, in its saved place in the order.
