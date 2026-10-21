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
      place: web::new-project
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

# Open New Project from the Command Palette

## Trigger

The User chooses New Project in the Command Palette.

## Outcome

New Project opens for the active workspace.
