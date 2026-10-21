---
kind: primary
routes:
  main: Main path
steps:
- text: The User switches the completed-work display on or off.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::settings
- text: The Product saves the Preferences on this device.
  kind: product
  entities:
  - entity: preferences
    effect: changes
    facts:
    - Show completed
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
  target: src/lib/store/appStore.ts#useAppStore
---

# Show or hide completed items

## Trigger

The User switches Show Completed Items in Settings.

## Outcome

The preference is kept on this device, and the item list reloads with completed items shown or left out.
