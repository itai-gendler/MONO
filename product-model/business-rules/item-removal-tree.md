---
appliesTo:
- type: capability
  id: delete-item
  contexts:
  - place: web
references:
- kind: code
  role: implementation
  target: src/lib/db/items.ts#deleteItem
---

# Deleting an item removes its descendants and checklist

Permanent local deletion recursively removes child items and each affected item’s checklist entries. Attached files belong to the removed item.
