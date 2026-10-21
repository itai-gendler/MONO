---
kind: primary
routes:
  main: Main path
steps:
- text: The User picks an icon and enters a name.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::new-project
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
references:
- kind: code
  role: implementation
  target: src/components/layout/CreateProjectModal.tsx#CreateProjectModal
- kind: code
  role: implementation
  target: src/lib/db/workspaces.ts#createProject
---

# Create and enter a project

## Trigger

The User chooses New Project in an active workspace.

## Outcome

The new project is selected; its items are listed and new captures go into it.

## Edge cases

- A nonblank name and active workspace are required.
- A creation failure is shown and the form remains available.
