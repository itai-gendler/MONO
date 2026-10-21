---
kind: primary
routes:
  main: Main path
steps:
- text: The User selects an extension to install.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::plugins
- text: The Product initializes and installs the Plugin.
  kind: product
  entities:
  - entity: plugin
    effect: creates
    facts:
    - Name
    - Description
    - Version
    - Activation
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

# Install an available extension

## Trigger

The User selects Install for a valid, available extension with the server connected.

## Outcome

The runtime initializes the extension and it joins the installed list.
