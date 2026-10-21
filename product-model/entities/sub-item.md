---
references:
- kind: code
  role: implementation
  target: src/lib/db/items.ts#createSubItem
- kind: code
  role: implementation
  target: src/components/items/ChecklistManager.tsx#ChecklistManager
---

# Sub-item

An individually completed checklist entry belonging to an item.

## Information kept

- **Title** — The checklist entry text.
- **Order** — Position in its parent’s checklist.
- **Created at** — When it was added.
- **Updated at** — When its completion changed.

## States

### Incomplete

An entry still to do.

### Completed

An entry marked done.
