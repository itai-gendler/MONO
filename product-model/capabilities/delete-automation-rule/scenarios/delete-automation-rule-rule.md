---
kind: primary
routes:
  main: Main path
steps:
- text: The User chooses Delete for an Automation Rule.
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
- text: The Product removes the Automation Rule.
  kind: product
  entities:
  - entity: automation-rule
    effect: removes
    from: Enabled
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

# Delete a saved rule

## Trigger

The User chooses Delete for a rule.

## Outcome

The rule is gone and no longer applies to captures.
