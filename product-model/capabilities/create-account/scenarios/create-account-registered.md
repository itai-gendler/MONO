---
kind: primary
routes:
  main: Main path
steps:
- text: The User supplies registration details.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: server-api::public
- text: The Product creates an Account and its owned Workspace named Personal Workspace.
  kind: product
  entities:
  - entity: account
    effect: creates
    facts:
    - Email
    - Name
    - Password
    - Avatar
  - entity: workspace
    effect: creates
    with: account
    facts:
    - Name
    - Icon
    - Created at
    - Updated at
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

# Register a server account

## Trigger

The User supplies a new valid email, name, and password.

## Outcome

An account and its Personal Workspace are created, and the response includes profile information and access credentials.
