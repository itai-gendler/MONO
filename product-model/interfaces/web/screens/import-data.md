---
entities:
- entity: item
  collects:
  - Title
  - Notes
  - Type
  - Priority
  - Tags
references:
- kind: code
  role: implementation
  target: src/components/ImportExport/ImportDialog.tsx#ImportDialog
---

# Import Data

Select a JSON file to add items or restore local workspaces, then read the import result.
