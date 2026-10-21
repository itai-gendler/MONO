---
kind: primary
routes:
  main: Main path
steps:
- text: The User picks the settings command.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::command-palette
- text: The Product opens Settings.
  kind: product
  entities: []
  actor: user
  contexts:
    main:
      place: web::settings
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

# Open Settings from the Command Palette

## Trigger

The User chooses Open Settings in the Command Palette.

## Outcome

Settings opens.
