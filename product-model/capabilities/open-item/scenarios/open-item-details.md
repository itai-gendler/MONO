---
kind: primary
routes:
  view: Item view
  search: Workspace search
steps:
- text: The User selects an Item.
  kind: actor
  entities:
  - entity: item
    effect: reads
    facts:
    - Title
  actor: user
  contexts:
    view:
      place: web::workspace
    search:
      place: web::command-palette
- text: The Product opens Item Details and loads the Item, Sub-items, and Attachments.
  kind: product
  entities:
  - entity: item
    effect: reads
    facts:
    - Title
    - Notes
    - Priority
    - Due date
    - Tags
    - Properties
  - entity: sub-item
    effect: reads
    facts:
    - Title
    - Order
  - entity: attachment
    effect: reads
    facts:
    - Name
    - Media type
    - Size
    - Contents
  actor: user
  contexts:
    view:
      place: web::item-details
    search:
      place: web::item-details
references:
- kind: code
  role: implementation
  target: src/components/items/ItemDetailPanel.tsx#ItemDetailPanel
- kind: code
  role: implementation
  target: src/components/items/ItemRow.tsx#ItemRow
- kind: code
  role: implementation
  target: src/components/views/CalendarView/CalendarDayCell.tsx#CalendarDayCell
- kind: code
  role: implementation
  target: src/components/layout/CommandPalette.tsx#CommandPalette
---

# Open a selected item

## Trigger

The User selects an item from a view or search result.

## Outcome

Item Details is ready for reading and editing the same item.

## Edge cases

- A missing item produces no editable details.
