---
appliesTo:
- type: capability
  id: create-workspace
  contexts:
  - place: web
- type: capability
  id: create-project
  contexts:
  - place: web
- type: capability
  id: create-item
  contexts:
  - place: web
- type: capability
  id: add-sub-item
  contexts:
  - place: web
- type: capability
  id: edit-item
  contexts:
  - place: web
references:
- kind: code
  role: implementation
  target: src/app/app/page.tsx#CreateWorkspaceModal
- kind: code
  role: implementation
  target: src/components/layout/CreateProjectModal.tsx#CreateProjectModal
- kind: code
  role: implementation
  target: src/components/items/QuickCapture.tsx#QuickCapture
- kind: code
  role: implementation
  target: src/components/items/ItemDetailPanel.tsx#ItemDetailPanel
- kind: code
  role: implementation
  target: src/components/items/ChecklistManager.tsx#ChecklistManager
---

# Local workspace, project, item, and checklist names must be nonblank

Browser naming and capture forms trim names and titles. Blank local names cannot be submitted; a blank title edit does not replace the stored item title.
