---
acts: external
kind: person
relations:
- entity: account
  verb: holds
  cardinality: one-to-one
references:
- kind: code
  role: implementation
  target: src/app/app/page.tsx#Home
- kind: code
  role: implementation
  target: server/src/auth/auth.controller.ts#AuthController
---

# User

A person using MONO to organize their work, either locally or through a server account.
