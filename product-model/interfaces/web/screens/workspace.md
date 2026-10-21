---
entities:
- entity: workspace
  shows:
  - Name
  - Icon
- entity: project
  shows:
  - Name
  - Icon
- entity: item
  shows:
  - Title
  - Notes
  - Priority
  - Due date
  - Tags
  collects:
  - Title
  - Priority
  - Due date
  - Tags
- entity: saved-filter
  shows:
  - Name
  - Criteria
  collects:
  - Name
references:
- kind: code
  role: implementation
  target: src/app/app/page.tsx#AppShell
- kind: code
  role: implementation
  target: src/components/views/ListView.tsx#ListView
- kind: code
  role: implementation
  target: src/components/views/BoardView/BoardView.tsx#BoardView
- kind: code
  role: implementation
  target: src/components/views/CalendarView/CalendarView.tsx#CalendarView
- kind: code
  role: implementation
  target: src/components/views/TimelineView/TimelineView.tsx#TimelineView
---

# Workspace

The active workspace or project and its items. List, board, calendar, and timeline are ways of examining this same subject.
