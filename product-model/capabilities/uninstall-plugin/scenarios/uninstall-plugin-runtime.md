---
kind: primary
routes:
  main: Main path
steps:
- text: The User selects a Plugin to uninstall.
  kind: actor
  entities:
  - entity: plugin
    effect: reads
    facts:
    - Name
  actor: user
  contexts:
    main:
      place: web::plugins
- text: The Product removes the Plugin after its deactivation completes.
  kind: product
  entities:
  - entity: plugin
    effect: removes
  actor: user
  contexts:
    main:
      place: web::plugins
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
---

# Uninstall an extension

## Trigger

The User chooses Uninstall for an installed extension with the server connected.

## Outcome

The extension is deactivated for the selected workspace and removed from the runtime registry.
