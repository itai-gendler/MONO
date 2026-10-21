---
kind: validation
routes:
  main: Main path
steps:
- text: The User submits credentials.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: server-api::public
- text: The Product reports invalid credentials.
  kind: product
  entities: []
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

# Refuse invalid credentials

## Trigger

The email is unknown or the password does not match.

## Outcome

The server reports Invalid email or password.
