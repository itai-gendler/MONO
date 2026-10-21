---
kind: primary
routes:
  main: Main path
steps:
- text: The User supplies credentials.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: server-api::public
- text: The Product validates the Account credentials and returns its profile.
  kind: product
  entities:
  - entity: account
    effect: reads
    facts:
    - Email
    - Password
    - Name
    - Avatar
  actor: user
  contexts:
    main:
      place: server-api::public
references:
- kind: code
  role: implementation
  target: server/src/auth/auth.controller.ts#AuthController
- kind: code
  role: implementation
  target: server/src/auth/auth.service.ts#AuthService
---

# Sign in to an account

## Trigger

The User submits the registered email and password.

## Outcome

The server returns access credentials and profile information.
