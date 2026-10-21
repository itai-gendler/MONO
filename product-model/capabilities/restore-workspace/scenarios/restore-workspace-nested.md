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
    as: previous
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
    as: parent
  - entity: attachment
    effect: creates
    with: parent
    facts:
    - Name
    - Media type
    - Size
    - Contents
    - Added at
  - entity: item
    as: child
    effect: creates
    to: Completed
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
    with: parent
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

# Restore a nested item collection

## Trigger

The User restores a valid local backup containing an active parent and a completed child.

## Outcome

The workspace, project, and item collections are replaced by the backup. The parent-child relation, sibling positions, completed child’s timestamp, and attached files are preserved. The first restored workspace becomes active.
