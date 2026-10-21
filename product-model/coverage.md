---
scope: The local workspace UI, shared item editing, files and checklists, data transfer, automation definitions, plugin lifecycle, and the account registration, sign-in and profile API.
method: Static reading of tracked source at 359a2da90fe15882d04ffcfef8e49ac2cbf64549, starting from the README, docs and the UI and API entry points.
covered:
- description: Local application entry, workspace and project creation, capture, and item views.
  paths:
  - src/app/app/
  - src/components/views/
  - src/components/items/
  - src/lib/db/
  - src/lib/search/
  - src/lib/types/
  - src/lib/utils/date.ts
- description: Workspace navigation, command palette, settings, data import and export, and the install prompt.
  paths:
  - src/components/layout/
  - src/components/ImportExport/
  - src/lib/store/appStore.ts
  - src/lib/hooks/usePWA.ts
  - public/sw.js
- description: Automation rules and their evaluation, plugin operations, and productivity insights.
  paths:
  - src/components/automation/
  - src/lib/automation/
  - src/lib/store/automationStore.ts
  - src/components/plugins/
  - server/src/plugins/
  - src/components/intelligence/
  - src/lib/intelligence/
- description: Server account registration, sign-in, default workspace and profile.
  paths:
  - server/src/auth/
  - server/prisma/schema.prisma
exclusions:
- description: Marketing page, search metadata, styles and static assets.
  paths:
  - src/app/page.tsx
  - src/app/layout.tsx
  - src/app/robots.ts
  - src/app/sitemap.ts
  - src/app/manifest.ts
  - src/styles/
  - src/app/globals.css
  - public/
  - docs/seo/
- description: Build tooling, journal automation, CI and developer setup.
  paths:
  - scripts/
  - .github/
  - docs/DEVELOPER_JOURNAL.md
  - activity_log.json
  - package.json
  - server/package.json
- description: Generic UI widgets, shortcut notation and screen-size helpers.
  paths:
  - src/components/ui/
  - src/lib/utils/keyboard.ts
  - src/lib/hooks/useIsMobile.ts
unmapped:
- description: Item store history helpers.
  paths:
  - src/lib/store/itemStore.ts
- description: Client synchronization helpers and the server real-time gateway.
  paths:
  - src/lib/sync/
  - server/src/sync/
- description: Item reordering, archiving, nesting, recurrence and project editing helpers.
  paths:
  - src/lib/db/items.ts
  - src/lib/db/workspaces.ts
  - src/lib/utils/recurring.ts
- description: Tag management, browser account, membership invitation and workspace member components.
  paths:
  - src/components/layout/TagManagerModal.tsx
  - src/lib/db/tags.ts
  - src/components/layout/AuthModal.tsx
  - src/lib/store/authStore.ts
  - src/components/layout/InviteMemberModal.tsx
- description: Item activity feed and the sidebar's Today and Favorites entries.
  paths:
  - src/components/items/ActivityFeed.tsx
  - src/components/layout/Sidebar.tsx
- description: Plugin widget host and pattern recognition helpers.
  paths:
  - src/components/plugins/PluginWidgetHost.tsx
  - src/lib/intelligence/patternRecognition.ts
- description: Server workspace, item, membership, import and export API modules.
  paths:
  - server/src/api/
  - server/src/items/
  - server/src/workspaces/
  - server/src/import-export/
- description: Web app API routes and their controllers and services.
  paths:
  - src/app/api/
  - src/lib/api/
limitations: []
---

# Coverage
