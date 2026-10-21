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
- kind: code
  role: implementation
  target: server/src/auth/dto/register.dto.ts#RegisterDto
---

# Create account

Register a server account with a name, email, and password and receive a Personal Workspace.
