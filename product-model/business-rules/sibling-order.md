---
appliesTo:
- type: capability
  id: create-item
  contexts:
  - place: web
- type: capability
  id: add-sub-item
  contexts:
  - place: web
references:
- kind: code
  role: implementation
  target: src/lib/db/items.ts#createItem
- kind: code
  role: implementation
  target: src/lib/db/items.ts#createSubItem
- kind: code
  role: implementation
  target: src/lib/db/items.ts#listSubItems
---

# New local entries follow their siblings

Newly captured local items and checklist entries receive the next position after the greatest existing sibling order. Checklist reads sort by that position.
