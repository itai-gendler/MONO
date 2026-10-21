---
kind: primary
routes:
  main: Main path
steps:
- text: The User switches the view to Calendar and picks a month.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product places each dated Item on its due day and counts the items on each day.
  kind: product
  entities:
  - entity: item
    effect: reads
    facts:
    - Title
    - Due date
  actor: user
  contexts:
    main:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: src/components/views/CalendarView/CalendarDayCell.tsx#CalendarDayCell
---

# Read a month on the calendar

## Trigger

The User chooses Calendar and moves to a month.

## Outcome

Each day of the month shows the items due that day and how many there are; items without a due date are not on the calendar.

## Edge cases

- A month with no dated items shows empty days.
