---
domain: automations
references:
- kind: code
  role: implementation
  target: src/lib/store/automationStore.ts#useAutomationStore
- kind: code
  role: implementation
  target: src/lib/automation/ruleEngine.ts#evaluateAutomations
---

# Automation rule

A named IF/THEN instruction evaluated during Quick Capture.

## Information kept

- **Name** — The rule’s name.
- **Trigger** — Status equals, priority equals, or has tag, with a matching value.
- **Action** — Add tag, set priority, or set due date, with a value.
- **Created at** — When it was created.

## States

### Enabled

The rule participates in capture evaluation.

### Disabled

The rule is retained but skipped during evaluation.
