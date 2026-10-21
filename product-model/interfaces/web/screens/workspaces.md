---
entities:
- entity: workspace
  shows:
  - Name
  - Icon
  collects:
  - Name
  - Icon
references:
- kind: code
  role: implementation
  target: src/components/layout/WorkspaceSwitcher.tsx#WorkspaceSwitcher
- kind: code
  role: implementation
  target: src/app/app/page.tsx#OnboardingScreen
---

# Workspaces

Choose a local workspace or create a new one. First-run template choice and workspace naming are one creation process.
