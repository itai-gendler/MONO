---
appliesTo:
- type: entity
  id: item
  effect: changes
  facts:
  - Completed at
references:
- kind: code
  role: implementation
  target: src/lib/db/items.ts#completeItem
- kind: code
  role: implementation
  target: src/lib/db/items.ts#restoreItem
- kind: code
  role: implementation
  target: src/components/views/BoardView/BoardView.tsx#BoardView
---

# Completion records a time and restoration clears it

Completing an item records its completion time. Returning it to Active or In Progress clears that time.
