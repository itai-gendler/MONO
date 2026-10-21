---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/lib/db/items.ts#deleteItem
- kind: code
  role: implementation
  target: src/components/items/ItemDetailPanel.tsx#ItemDetailPanel
- kind: code
  role: implementation
  target: src/components/layout/BatchActionBar.tsx#BatchActionBar
---

# Delete item

Permanently remove an item, including nested children and checklist entries, from local storage.
