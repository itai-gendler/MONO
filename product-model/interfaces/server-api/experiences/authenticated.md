---
actors:
- user
access: authenticated
references:
- kind: code
  role: implementation
  target: server/src/auth/auth.controller.ts#AuthController
---

# Account profile

The current profile for a signed-in person.
