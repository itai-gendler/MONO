---
kind: primary
routes:
  main: Main path
steps:
- text: The User chooses Markdown export.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product renders the workspace Items into Markdown.
  kind: product
  entities:
  - entity: item
    effect: reads
    facts:
    - Title
    - Type
    - Priority
    - Tags
    - Notes
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
  target: src/components/ImportExport/ExportButton.tsx#ExportButton
- kind: code
  role: implementation
  target: src/lib/db/backup.ts#exportWorkspaceBackup
---

# Export workspace notes as Markdown

## Trigger

The User chooses Markdown export.

## Outcome

The download contains each available item’s title, completion marker, type, status, priority, tags, and notes in the active workspace.
