---
kind: primary
routes:
  main: Main path
steps:
- text: The browser has offered installation and the app is not already installed.
  kind: condition
  entities: []
  contexts:
    main:
      place: web::workspace
- text: The User chooses Install and accepts the browser request.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::workspace
- text: The Product recognizes the browser’s accepted installation outcome.
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

# Install the application

## Trigger

The browser offers installation and the User chooses Install.

## Outcome

After accepting the browser prompt, MONO is marked installed and its install offer disappears.
