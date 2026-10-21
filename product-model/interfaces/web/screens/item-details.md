---
entities:
- entity: item
  shows:
  - Title
  - Notes
  - Priority
  - Due date
  - Tags
  - Properties
  collects:
  - Title
  - Notes
  - Priority
  - Due date
  - Tags
  - Properties
- entity: sub-item
  shows:
  - Title
  - Order
  collects:
  - Title
- entity: attachment
  shows:
  - Name
  - Media type
  - Size
  - Contents
  collects:
  - Contents
references:
- kind: code
  role: implementation
  target: src/components/items/ItemDetailPanel.tsx#ItemDetailPanel
---

# Item Details

One selected item, its editable notes and attributes, checklist entries, and attached files.
