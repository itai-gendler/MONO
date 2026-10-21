---
appliesTo:
- type: entity
  id: sub-item
references:
- kind: code
  role: implementation
  target: src/components/items/ChecklistManager.tsx#ChecklistManager
- kind: code
  role: implementation
  target: src/components/items/ItemDetailPanel.tsx#ItemDetailPanel
---

# Checklist progress counts completed entries

Progress is completed entries divided by all entries, rounded to a percentage. An empty checklist has zero progress. Changing checklist completion does not change the parent item’s completion.
