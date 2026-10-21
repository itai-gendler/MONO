---
availability:
- place: server-api::public
references:
- kind: code
  role: implementation
  target: server/src/auth/auth.controller.ts#AuthController
- kind: code
  role: implementation
  target: server/src/auth/auth.service.ts#AuthService
---

# Sign in

Exchange valid server account credentials for access credentials and profile information.
