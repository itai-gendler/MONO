---
kind: primary
result: achieved
routes:
  main: Web
steps:
- text: The User picks the matching command in the Command Palette.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::command-palette
  capability: browse-commands
- text: The Product opens the naming form.
  kind: product
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspaces
  capability: browse-commands
- text: The User picks an icon and enters a name.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspaces
  capability: create-workspace
- text: The Product creates the Workspace and makes it active.
  kind: product
  entities:
  - entity: workspace
    effect: creates
    facts:
    - Name
    - Icon
    - Order
    - Created at
    - Updated at
  actor: user
  contexts:
    main:
      place: web::workspace
  capability: create-workspace
references:
- kind: code
  role: implementation
  target: src/components/layout/CommandPalette.tsx#useCommandItems
- kind: code
  role: implementation
  target: src/app/app/page.tsx#CreateWorkspaceModal
- kind: code
  role: implementation
  target: src/lib/db/workspaces.ts#createWorkspace
---

# Create a workspace from the Command Palette

## Trigger

The User opens the Command Palette and chooses New Workspace.

## Outcome

The workspace is created and becomes the active workspace, with no project selected.
