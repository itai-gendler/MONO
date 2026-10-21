---
appliesTo:
- type: entity
  id: automation-rule
- type: capability
  id: create-item
  contexts:
  - place: web
references:
- kind: code
  role: implementation
  target: src/lib/automation/ruleEngine.ts#evaluateAutomations
- kind: code
  role: implementation
  target: src/components/items/QuickCapture.tsx#QuickCapture
---

# Enabled capture rules run in saved order

Only enabled rules participate. Each rule sees the result of earlier rules; a matching rule can add a missing tag, change priority, or set a parsable due date.
