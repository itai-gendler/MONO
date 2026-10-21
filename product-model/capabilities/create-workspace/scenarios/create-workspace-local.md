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
      place: web::workspaces
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
references:
- kind: code
  role: implementation
  target: src/app/app/page.tsx#OnboardingScreen
- kind: code
  role: implementation
  target: src/app/app/page.tsx#CreateWorkspaceModal
- kind: code
  role: implementation
  target: src/lib/db/workspaces.ts#createWorkspace
---

# Create and enter a workspace

## Trigger

The User chooses a first-run template or New Workspace.

## Outcome

The new workspace is active with no project selected, ready for its first items.

## Edge cases

- Templates prefill the name and icon; they do not seed projects or tasks.
- A whitespace-only name cannot be submitted.
