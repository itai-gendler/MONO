---
entities:
- entity: plugin
  shows:
  - Name
  - Description
  - Version
  - Activation
references:
- kind: code
  role: implementation
  target: src/components/plugins/PluginList.tsx#PluginList
- kind: code
  role: implementation
  target: src/components/plugins/PluginStore.tsx#PluginStore
---

# Plugins

Discover extensions and inspect installed extensions and their activation for the selected workspace.
