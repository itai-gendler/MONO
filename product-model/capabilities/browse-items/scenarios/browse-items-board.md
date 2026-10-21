---
kind: primary
routes:
  main: Main path
steps:
- text: The User switches the view to Board.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product groups the Items into To Do, In Progress and Completed columns by status.
  kind: product
  entities:
  - entity: item
    effect: reads
    facts:
    - Title
    - Priority
    - Due date
    - Tags
  actor: user
  contexts:
    main:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: src/components/views/BoardView/BoardView.tsx#BoardView
- kind: code
  role: implementation
  target: src/lib/types/view.ts#DEFAULT_BOARD_COLUMNS
---

# Read the board

## Trigger

The User chooses Board for the active workspace or project.

## Outcome

Each item appears once, in the column for its status: To Do for Active items, then In Progress and Completed.

## Edge cases

- With no matching items, every column is empty.
