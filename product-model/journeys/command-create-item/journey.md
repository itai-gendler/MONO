---
actors:
- user
references:
- kind: code
  role: implementation
  target: src/components/layout/CommandPalette.tsx#useCommandItems
- kind: code
  role: implementation
  target: src/components/items/QuickCapture.tsx#QuickCapture
---

# Capture a task from the Command Palette

## Goal

The User wants to capture a task without leaving the keyboard.

## Success criterion

A new task is saved in the active workspace or project.
