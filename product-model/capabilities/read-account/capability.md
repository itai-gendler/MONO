---
availability:
- place: server-api::authenticated
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

# Read account

Read the profile of the account represented by the current server session.
