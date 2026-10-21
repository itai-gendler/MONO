---
id: mono
summary: A local-first personal workspace unifying tasks, notes, projects, and goals.
category: productivity
tags:
- local-first
- tasks
- notes
- workspace
authors:
- name: Siddhant Bhatia
  url: https://github.com/siddhantbhatia220
license: MIT
languages:
- en
limitations:
- Quick Capture creates tasks; other item types can arrive through item import.
- The timeline covers fourteen days beginning on Monday of the current week.
- Workspaces, projects and items are kept in the browser on the device where they are created; a JSON backup carries them to another device.
- The local workspace needs no account; registering and signing in to a server account happen through the Account API, separately from the local workspace.
references:
- kind: doc
  role: intent
  target: README.md
- kind: code
  role: implementation
  target: src/app/app/page.tsx#Home
- kind: code
  role: implementation
  target: src/components/items/QuickCapture.tsx#QuickCapture
- kind: code
  role: implementation
  target: src/components/views/TimelineView/TimelineView.tsx#TimelineView
- kind: code
  role: implementation
  target: src/lib/db/backup.ts#exportWorkspaceBackup
---

# MONO

MONO is a local-first personal workspace. People capture tasks with Quick Capture, keep notes, checklists and files on each item, organize items into workspaces and projects, and review the same items as a list, a board, a calendar or a timeline. Everything is kept in the browser on the person's device, works offline once installed, and moves between devices as a JSON backup. A separate Account API registers server accounts, signs them in and returns their profile.

## Intent

The README describes MONO as “a privacy-focused, keyboard-first workspace unifying tasks, notes, projects, and goals”, an open-source, local-first Personal Operating System “engineered for speed, privacy, and focus”. Its Universal Item Model “eliminates arbitrary silos between tasks, notes, goals, bookmarks, and events — allowing all data to coexist in a single source of truth”, so the same items can be viewed as a list, a board, a calendar or a timeline. Data stays on the device, and every action is reachable from the keyboard.
