---
kind: primary
routes:
  main: Main path
steps:
- text: The User selects a catalog category or search query.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::plugins
- text: The Product presents the matching catalog choices and installed Plugins.
  kind: product
  entities:
  - entity: plugin
    effect: reads
    facts:
    - Name
    - Description
    - Version
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

# Browse extension choices

## Trigger

The User opens Plugins.

## Outcome

The catalog can be searched and filtered, and connected-runtime installations show their names, descriptions, and versions.

## Edge cases

- An empty installed list offers catalog discovery.
