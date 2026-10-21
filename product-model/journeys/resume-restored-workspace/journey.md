---
actors:
- user
references:
- kind: code
  role: implementation
  target: src/components/ImportExport/ImportDialog.tsx#ImportDialog
- kind: code
  role: implementation
  target: src/lib/db/backup.ts#restoreWorkspaceBackup
---

# Restore a backup and continue working

## Goal

The User wants to continue on this device with the workspaces from a backup.

## Success criterion

The backup's first workspace is active and its items are listed.
