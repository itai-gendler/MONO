---
type: web
actors:
- user
entryPoints:
- web: /app
references:
- kind: code
  role: implementation
  target: src/app/app/page.tsx#Home
---

# Web

The local workspace in a browser, including its installable web application. The workspace is usable without a server account.
