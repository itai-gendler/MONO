---
kind: primary
routes:
  main: Main path
steps:
- text: The User picks the keyboard help command.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::command-palette
- text: The Product presents the shortcut guide.
  kind: product
  entities: []
  actor: user
  contexts:
    main:
      place: web
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

# Open the shortcut guide

## Trigger

The User chooses Keyboard Shortcuts in the Command Palette, or presses ? outside a text field.

## Outcome

The guide lists every shortcut by category.
