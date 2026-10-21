---
relations:
- entity: workspace
  verb: owns
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: server/src/auth/auth.service.ts#AuthService
- kind: code
  role: implementation
  target: server/src/auth/dto/register.dto.ts#RegisterDto
---

# Account

A registered identity for the MONO server.

## Information kept

- **Email** — The registered email address, normalized to lowercase.
- **Name** — The person’s supplied name.
- **Password** — The credential supplied for registration and sign-in.
- **Avatar** — An optional profile image address.
