---
kind: primary
routes:
  main: Main path
steps:
- text: The User chooses JSON export.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product reads Workspaces, Projects, Items, and Attachments for the download.
  kind: product
  entities:
  - entity: workspace
    effect: reads
    facts:
    - Name
    - Icon
    - Order
    - Created at
    - Updated at
  - entity: project
    effect: reads
    facts:
    - Name
    - Icon
    - Order
    - Created at
    - Updated at
  - entity: item
    effect: reads
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
    effect: reads
    facts:
    - Name
    - Media type
    - Size
    - Contents
    - Added at
  actor: user
  contexts:
    main:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: src/components/ImportExport/ExportButton.tsx#ExportButton
- kind: code
  role: implementation
  target: src/lib/db/backup.ts#exportWorkspaceBackup
---

# Export local workspaces as JSON

## Trigger

The User chooses JSON export.

## Outcome

A dated JSON backup contains all local workspaces, projects, and items.
