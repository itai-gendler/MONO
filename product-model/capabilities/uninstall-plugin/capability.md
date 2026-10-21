---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: src/components/plugins/PluginList.tsx#PluginList
- kind: code
  role: implementation
  target: src/components/plugins/PluginStore.tsx#PluginStore
- kind: code
  role: implementation
  target: server/src/plugins/plugins.service.ts#PluginsService
- kind: code
  role: implementation
  target: server/src/plugins/plugins.controller.ts#PluginsController
domain: plugins
---

# Uninstall plugin

Deactivate an extension for the selected workspace and remove it from the installed runtime registry.
