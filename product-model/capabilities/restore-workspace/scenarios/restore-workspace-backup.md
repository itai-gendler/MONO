---
kind: primary
routes:
  main: Main path
steps:
- text: The User chooses a full backup.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::import-data
- text: The Product removes existing Workspaces, Projects, and Items.
  kind: product
  entities:
  - entity: workspace
    effect: removes
  - entity: project
    effect: removes
    with: workspace
  - entity: item
    effect: removes
    from: Active
    with: workspace
  actor: user
  contexts:
    main:
      place: web::import-data
- text: The Product restores Workspaces, Projects, Items, and Attachments from the backup.
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
  - entity: project
    effect: creates
    with: workspace
    facts:
    - Name
    - Icon
    - Order
    - Created at
    - Updated at
  - entity: item
    effect: creates
    to: Active
    with: workspace
    facts:
    - Title
    - Notes
    - Content
    - Type
    - Priority
    - Due date
    - Tags
    - Properties
    - Placement
    - Order
    - Pinned
    - Completed at
    - Created at
    - Updated at
  - entity: attachment
    effect: creates
    with: item
    facts:
    - Name
    - Media type
    - Size
    - Contents
    - Added at
  actor: user
  contexts:
    main:
      place: web::import-data
- text: The Product selects the first restored Workspace.
  kind: product
  entities:
  - entity: workspace
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    main:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: src/components/ImportExport/ImportDialog.tsx#ImportDialog
- kind: code
  role: implementation
  target: src/lib/db/backup.ts#restoreWorkspaceBackup
---

# Restore a full local backup

## Trigger

The User imports a valid MONO backup with workspace and item collections.

## Outcome

The backup replaces those local collections, retaining item identities, notes, scheduling, hierarchy, and attachments. Its first workspace becomes active.
