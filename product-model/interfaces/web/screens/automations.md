---
entities:
- entity: automation-rule
  shows:
  - Name
  - Trigger
  - Action
  collects:
  - Name
  - Trigger
  - Action
references:
- kind: code
  role: implementation
  target: src/components/automation/AutomationModal.tsx#AutomationModal
---

# Visual Automations

Read and create rules and control whether they participate in capture.
