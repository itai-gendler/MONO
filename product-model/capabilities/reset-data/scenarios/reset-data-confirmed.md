---
kind: primary
routes:
  main: Main path
steps:
- text: The User chooses Reset all data and confirms.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::settings
- text: The Product removes Workspaces, Projects, Items, Sub-items, Attachments, Preferences, Saved Filters, and Automation Rules.
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
  - entity: sub-item
    effect: removes
    from: Incomplete
    with: item
  - entity: attachment
    effect: removes
    with: item
  - entity: preferences
    effect: removes
  - entity: saved-filter
    effect: removes
  - entity: automation-rule
    effect: removes
    from: Enabled
  actor: user
  contexts:
    main:
      place: web::settings
references:
- kind: code
  role: implementation
  target: src/components/layout/SettingsModal.tsx#SettingsModal
- kind: code
  role: implementation
  target: src/lib/db/index.ts#getDB
---

# Reset local application data

## Trigger

The User chooses Reset all data in Settings and confirms.

## Outcome

Local workspaces, projects, items, checklists, preferences, saved filters and rules are cleared, and MONO reloads into first-run setup.

## Edge cases

- Cancelling confirmation preserves local data.
- A failed database deletion is reported.
