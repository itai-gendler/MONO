---
references:
- kind: code
  role: implementation
  target: src/lib/store/appStore.ts#useAppStore
- kind: code
  role: implementation
  target: src/components/views/SearchView/SmartFilterBar.tsx#SmartFilterBar
---

# Saved filter

A named reusable set of item search criteria.

## Information kept

- **Name** — A person-supplied name.
- **Criteria** — Search text, status, priority, tags, and pinned-only criteria captured together.
- **Created at** — When the filter was saved.
