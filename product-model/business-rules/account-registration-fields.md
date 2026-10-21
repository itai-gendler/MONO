---
appliesTo:
- type: entity
  id: account
  effect: creates
references:
- kind: code
  role: implementation
  target: server/src/auth/dto/register.dto.ts#RegisterDto
- kind: code
  role: implementation
  target: server/src/main.ts#bootstrap
---

# Registration needs a valid email, name, and password of at least eight characters

Server registration validates a nonempty name and valid email and requires a password with at least eight characters.
