---
domain: plugins
references:
- kind: code
  role: implementation
  target: server/src/plugins/plugins.service.ts#PluginsService
- kind: code
  role: implementation
  target: src/components/plugins/PluginList.tsx#PluginList
---

# Plugin

An extension installed in the MONO server runtime, which can be activated for a workspace.

## Information kept

- **Name** — Display name.
- **Description** — What the extension provides.
- **Version** — The extension version when supplied.
- **Activation** — Whether the extension is active for the selected workspace.
