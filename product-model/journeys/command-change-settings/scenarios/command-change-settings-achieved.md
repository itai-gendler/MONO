---
kind: primary
result: achieved
routes:
  main: Web
steps:
- text: The User picks the settings command in the Command Palette.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::command-palette
  capability: browse-commands
- text: The Product opens Settings.
  kind: product
  entities: []
  actor: user
  contexts:
    main:
      place: web::settings
  capability: browse-commands
- text: The User switches the completed-work display off.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::settings
  capability: change-settings
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
  capability: change-settings
references:
- kind: code
  role: implementation
  target: src/components/layout/CommandPalette.tsx#useCommandItems
- kind: code
  role: implementation
  target: src/components/layout/SettingsModal.tsx#SettingsModal
- kind: code
  role: implementation
  target: src/lib/store/appStore.ts#useAppStore
---

# Hide completed items from the Command Palette

## Trigger

The User opens the Command Palette and chooses Open Settings.

## Outcome

Show Completed Items is saved on this device and the list reloads to follow it.
