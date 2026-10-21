---
entities:
- entity: workspace
  shows:
  - Name
- entity: project
  collects:
  - Name
  - Icon
references:
- kind: code
  role: implementation
  target: src/components/layout/CreateProjectModal.tsx#CreateProjectModal
---

# New Project

Name a project in the active workspace.
