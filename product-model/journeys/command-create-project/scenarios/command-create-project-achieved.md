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
      place: web::new-project
  capability: browse-commands
- text: The User picks an icon and enters a name.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::new-project
  capability: create-project
- text: The Product creates the Project in the active workspace and selects it.
  kind: product
  entities:
  - entity: project
    effect: creates
    facts:
    - Name
    - Icon
    - Order
    - Created at
    - Updated at
  - entity: workspace
    effect: reads
    facts: []
  actor: user
  contexts:
    main:
      place: web::workspace
  capability: create-project
references:
- kind: code
  role: implementation
  target: src/components/layout/CommandPalette.tsx#useCommandItems
- kind: code
  role: implementation
  target: src/components/layout/CreateProjectModal.tsx#CreateProjectModal
- kind: code
  role: implementation
  target: src/lib/db/workspaces.ts#createProject
---

# Create a project from the Command Palette

## Trigger

The User opens the Command Palette and chooses New Project.

## Outcome

The project is created in the active workspace and selected, ready for its first task.
