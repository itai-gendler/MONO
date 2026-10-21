---
kind: primary
routes:
  main: Main path
steps:
- text: The User requests their Account profile.
  kind: actor
  entities:
  - entity: account
    effect: reads
    facts: []
  actor: user
  contexts:
    main:
      place: server-api::authenticated
- text: The Product returns the Account profile.
  kind: product
  entities:
  - entity: account
    effect: reads
    facts:
    - Email
    - Name
    - Avatar
  actor: user
  contexts:
    main:
      place: server-api::authenticated
references:
- kind: code
  role: implementation
  target: server/src/auth/auth.controller.ts#AuthController
- kind: code
  role: implementation
  target: server/src/auth/auth.service.ts#AuthService
- kind: code
  role: implementation
  target: server/src/auth/jwt.strategy.ts#JwtStrategy
---

# Read the current profile

## Trigger

The User requests their profile.

## Outcome

The response contains the current account’s email, name, and optional avatar.
