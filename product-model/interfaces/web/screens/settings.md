---
entities:
- entity: preferences
  shows:
  - Theme
  - Layout density
  - Show completed
  collects:
  - Theme
  - Layout density
  - Show completed
references:
- kind: code
  role: implementation
  target: src/components/layout/SettingsModal.tsx#SettingsModal
---

# Settings

Change the theme, layout density and completed-item display, or reset local data.
