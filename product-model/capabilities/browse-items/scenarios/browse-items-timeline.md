---
kind: primary
routes:
  main: Main path
steps:
- text: The User switches the view to Timeline.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product places each Item on its due date, or on its creation date when it has none, across fourteen days from this week's Monday.
  kind: product
  entities:
  - entity: item
    effect: reads
    facts:
    - Title
    - Due date
    - Created at
  actor: user
  contexts:
    main:
      place: web::workspace
references: []
---

# Read the two-week timeline

## Trigger

The User chooses Timeline.

## Outcome

Each item is a row placed on its day in the fourteen days that start on this week's Monday, with today marked.

## Edge cases

- With no matching items, the timeline has no rows.
