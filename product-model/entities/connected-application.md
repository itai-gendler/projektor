---
domain: connect-agent
references:
- kind: code
  role: implementation
  target: apps/api/src/services/oauth.ts#listConnectorGrants
- kind: code
  role: implementation
  target: apps/api/src/routes/oauth.ts
---

# Connected application

An application a person has allowed to reach one workspace on their behalf through the connector sign-in. It can never do more than that person can.

## Information kept

- **Application** — the application's self-declared name and its verified address
- **Access** — what it was allowed: read, or read and write
- **Connected at** — when the person allowed it
- **Expires at** — when the sign-in lapses unless renewed
