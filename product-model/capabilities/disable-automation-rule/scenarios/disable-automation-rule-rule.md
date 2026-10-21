---
kind: primary
routes:
  main: Main path
steps:
- text: The User switches an enabled Automation Rule off.
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
- text: The Product disables the Automation Rule.
  kind: product
  entities:
  - entity: automation-rule
    effect: changes
    from: Enabled
    to: Disabled
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

# Disable a saved rule

## Trigger

The User switches off an enabled rule in Visual Automations.

## Outcome

The rule stays in the list, disabled, and is skipped when items are captured.
