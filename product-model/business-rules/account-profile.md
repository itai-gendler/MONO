---
appliesTo:
- type: entity
  id: account
  effect: reads
  facts:
  - Email
  - Name
  - Avatar
  contexts:
  - place: server-api::authenticated
references:
- kind: code
  role: implementation
  target: server/src/auth/auth.controller.ts#AuthController
- kind: code
  role: implementation
  target: server/src/auth/jwt.strategy.ts#JwtStrategy
permits:
- related:
  - verb: holds
    entity: user
---

# Users read their own server account profile

The profile operation returns the account identified by the current authenticated session.
