---
kind: primary
routes:
  main: Main path
steps:
- text: The User chooses a theme and a layout density.
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
    - Theme
    - Layout density
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

# Change the theme and layout density

## Trigger

The User chooses Light, Dark or System, and Comfortable or Compact, in Settings.

## Outcome

MONO switches to the chosen theme and density at once and keeps them on this device; System follows the device's light or dark setting.
