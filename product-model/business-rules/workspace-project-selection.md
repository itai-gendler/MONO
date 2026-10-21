---
appliesTo:
- type: capability
  id: browse-workspaces
  contexts:
  - place: web
- type: capability
  id: create-workspace
  contexts:
  - place: web
- type: capability
  id: create-item
  contexts:
  - place: web
references:
- kind: code
  role: implementation
  target: src/lib/store/appStore.ts#useAppStore
- kind: code
  role: implementation
  target: src/components/items/QuickCapture.tsx#QuickCapture
---

# Choosing a workspace clears the selected project

Workspace choice clears the previous project selection so subsequent capture uses the newly selected workspace.
