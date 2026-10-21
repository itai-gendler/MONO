---
kind: primary
routes:
  main: Main path
steps:
- text: The User selects a Plugin to enable.
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
- text: The Product activates the Plugin for the selected workspace.
  kind: product
  entities:
  - entity: plugin
    effect: changes
    facts:
    - Activation
  - entity: workspace
    effect: reads
    facts: []
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

# Activate an installed extension

## Trigger

The User chooses Enable with the server connected and a workspace selected.

## Outcome

The extension receives workspace activation and the UI marks it active.
