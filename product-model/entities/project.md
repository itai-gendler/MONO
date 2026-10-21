---
relations:
- entity: item
  verb: contains
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/lib/db/workspaces.ts#createProject
- kind: code
  role: implementation
  target: src/components/layout/CreateProjectModal.tsx#CreateProjectModal
---

# Project

A named grouping of items within a workspace.

## Information kept

- **Name** — The project name.
- **Icon** — The icon chosen for the project when it is created.
- **Order** — Position among the workspace’s projects.
- **Created at** — When it was created.
- **Updated at** — When its record last changed.
