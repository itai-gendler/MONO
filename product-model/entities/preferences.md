---
singleton: true
domain: settings
references:
- kind: code
  role: implementation
  target: src/lib/store/appStore.ts#useAppStore
- kind: code
  role: implementation
  target: src/components/layout/SettingsModal.tsx#SettingsModal
---

# Preferences

The display preferences kept on this device.

## Information kept

- **Theme** — Light, dark, or following the system.
- **Layout density** — Comfortable or compact item rows.
- **Show completed** — Whether completed items are included in lists and projects.
