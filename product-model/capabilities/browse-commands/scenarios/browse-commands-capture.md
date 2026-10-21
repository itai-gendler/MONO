---
kind: primary
routes:
  main: Main path
steps:
- text: The User picks the capture command.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::command-palette
- text: The Product closes the palette and focuses Quick Capture.
  kind: product
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
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

# Start a capture from the Command Palette

## Trigger

The User opens the Command Palette and chooses New Item, or finds it by a keyword such as task or note.

## Outcome

Quick Capture is focused, ready for a new task.
