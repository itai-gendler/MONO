---
kind: primary
routes:
  main: Main path
steps:
- text: The User selects a Workspace.
  kind: actor
  entities:
  - entity: workspace
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    main:
      place: web::workspaces
- text: The Product reads the selected Workspace and its Projects.
  kind: product
  entities:
  - entity: workspace
    effect: reads
    facts:
    - Name
  - entity: project
    effect: reads
    facts:
    - Name
    - Order
  actor: user
  contexts:
    main:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: src/components/layout/WorkspaceSwitcher.tsx#WorkspaceSwitcher
- kind: code
  role: implementation
  target: src/lib/store/appStore.ts#useAppStore
- kind: code
  role: implementation
  target: src/components/layout/Sidebar.tsx#Sidebar
---

# Choose another workspace

## Trigger

The User opens the workspace chooser.

## Outcome

The chosen workspace becomes active and the previously selected project is cleared.
