---
kind: validation
routes:
  main: Main path
steps:
- text: The User supplies invalid registration details.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: server-api::public
- text: The Product reports the field validation failure.
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
- kind: code
  role: implementation
  target: server/src/auth/dto/register.dto.ts#RegisterDto
---

# Reject invalid registration fields

## Trigger

The email is invalid, the name is missing, or the password has fewer than eight characters.

## Outcome

Validation rejects the registration.
