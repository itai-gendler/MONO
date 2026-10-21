---
appliesTo:
- type: entity
  id: account
references:
- kind: code
  role: implementation
  target: server/src/auth/auth.service.ts#AuthService
---

# Server account email addresses are unique ignoring case

Registration lowercases the supplied email and rejects an address already registered. Sign-in uses the same lowercase lookup.
