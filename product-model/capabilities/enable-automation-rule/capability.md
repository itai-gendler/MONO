---
availability:
- place: web
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
domain: automations
---

# Enable automation rule

Include a saved rule in capture evaluation.
