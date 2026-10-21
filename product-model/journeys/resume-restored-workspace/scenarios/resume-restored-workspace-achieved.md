---
kind: primary
result: achieved
routes:
  main: Web
steps:
- text: The User chooses a MONO JSON backup in Import Data.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::import-data
  capability: restore-workspace
- text: The Product removes the local Workspaces, Projects and Items.
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
  capability: restore-workspace
- text: The Product restores the Workspaces, Projects and Items, with their Attachments, from the backup.
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
  capability: restore-workspace
- text: The Product makes the first restored Workspace active.
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
  capability: restore-workspace
- text: The User reads the restored Items.
  kind: actor
  entities:
  - entity: item
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    main:
      place: web::workspace
  capability: browse-items
references:
- kind: code
  role: implementation
  target: src/lib/db/backup.ts#restoreWorkspaceBackup
- kind: code
  role: implementation
  target: src/components/ImportExport/ImportDialog.tsx#ImportDialog
- kind: code
  role: implementation
  target: src/components/views/ListView.tsx#ListView
- kind: code
  role: implementation
  target: src/lib/db/items.ts#listItems
- kind: code
  role: implementation
  target: src/lib/search/fuzzySearch.ts#filterItems
- kind: code
  role: implementation
  target: src/components/layout/CommandPalette.tsx#CommandPalette
- kind: code
  role: implementation
  target: src/components/views/CalendarView/CalendarView.tsx#CalendarView
- kind: code
  role: implementation
  target: src/components/views/TimelineView/TimelineView.tsx#TimelineView
---

# Restore a backup on this device and continue

## Trigger

The User imports a MONO JSON backup in Import Data.

## Outcome

The backup's workspaces, projects and items are on this device, its first workspace is active, and its items are listed.
