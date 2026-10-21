---
kind: edge
routes:
  main: Main path
steps:
- text: The User dismisses the installation offer.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product hides the offer until MONO is reloaded.
  kind: product
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: src/lib/hooks/usePWA.ts#usePWA
- kind: code
  role: implementation
  target: src/components/layout/PWAInstallPrompt.tsx#PWAInstallPrompt
---

# Dismiss installation

## Trigger

The User dismisses the installation offer.

## Outcome

The current offer is hidden and workspace use continues.
