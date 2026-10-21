---
kind: primary
routes:
  main: Main path
steps:
- text: The User picks the matching command.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::command-palette
- text: The Product opens the naming form.
  kind: product
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspaces
references:
- kind: code
  role: implementation
  target: src/components/layout/CommandPalette.tsx#useCommandItems
- kind: code
  role: implementation
  target: src/components/layout/CommandPalette.tsx#CommandPalette
- kind: code
  role: implementation
  target: src/app/app/page.tsx#ShortcutsModal
---

# Open New Workspace from the Command Palette

## Trigger

The User chooses New Workspace in the Command Palette.

## Outcome

The New Workspace form opens.
