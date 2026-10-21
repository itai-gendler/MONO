---
relations:
- entity: project
  verb: contains
  cardinality: one-to-many
- entity: item
  verb: contains
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/lib/db/workspaces.ts#createWorkspace
- kind: code
  role: implementation
  target: server/src/workspaces/workspaces.service.ts#WorkspacesService
---

# Workspace

A named home for projects and items, such as Personal, Work or Study.

## Information kept

- **Name** — The workspace name.
- **Icon** — The icon chosen for the workspace when it is created.
- **Order** — Position in the list of workspaces; the first one opens when MONO starts.
- **Created at** — When the workspace was created.
- **Updated at** — When the workspace record last changed.
