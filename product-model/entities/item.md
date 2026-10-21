---
relations:
- entity: item
  verb: contains
  cardinality: one-to-many
- entity: sub-item
  verb: contains
  cardinality: one-to-many
- entity: attachment
  verb: contains
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/lib/types/item.ts#Item
- kind: code
  role: implementation
  target: src/lib/db/items.ts#createItem
- kind: code
  role: implementation
  target: src/components/views/BoardView/BoardView.tsx#BoardView
---

# Item

The shared thing used for tasks, notes, goals, events, habits, bookmarks, and checklists. These types share the same kept facts and detail editor.

## Information kept

- **Title** — The item’s name.
- **Notes** — Optional notes, including Markdown source, shared by every item type.
- **Content** — Optional Markdown content kept beside the notes, carried by backups and included in text matching; Item Details edits Notes, not Content.
- **Type** — Task, note, goal, event, habit, bookmark, or checklist.
- **Priority** — None, low, medium, high, or critical.
- **Due date** — An optional date used for scheduling.
- **Tags** — Labels used for organization and text matching.
- **Properties** — Named custom values.
- **Placement** — The workspace, optional project, and optional parent item to which it belongs.
- **Order** — Position among sibling items.
- **Pinned** — Whether the item is pinned; pinned items are listed first.
- **Completed at** — Completion time, cleared when returned to active work.
- **Created at** — Creation time.
- **Updated at** — Last modification time.

## States

### Active

Work ready to do, also called To Do on the board.

### In Progress

Work underway.

### Completed

Work marked done.
