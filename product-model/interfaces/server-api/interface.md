---
type: api
actors:
- user
entryPoints:
- api: /auth/register
- api: /auth/login
- api: /auth/me
references:
- kind: code
  role: implementation
  target: server/src/auth/auth.controller.ts#AuthController
---

# Account API

The MONO server account contract for registration, sign-in, and reading the current profile through an API client.
