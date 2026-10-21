---
kind: validation
routes:
  main: Main path
steps:
- text: The User submits registration details.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: server-api::public
- text: The Product detects the existing Account email and reports the conflict.
  kind: product
  entities:
  - entity: account
    effect: reads
    facts:
    - Email
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

# Refuse a duplicate email

## Trigger

The supplied email already belongs to an account, ignoring case.

## Outcome

Registration returns an existing-email conflict and creates nothing.
