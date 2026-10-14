---
singleton: true
references:
- kind: code
  role: implementation
  target: packages/types/src/env.ts
- kind: doc
  role: context
  target: apps/docs/src/content/docs/guides/deploying.md
  title: Deploying
---

# Deployment settings

The settings the operator gives the deployment outside the product, which decide who owns and who joins workspaces when they sign in, whether anonymous visitors may browse, and how long a file claim made without an agent session stays held.

## Information kept

- **Admin emails** — the people who own every workspace on the deployment
- **Default workspace** — the slug and name of the workspace the first admin sign-in creates and auto-join uses
- **Auto-join role** — the role a newly admitted person gets in the default workspace; none keeps the deployment invite-only
- **Workspace domain map** — email domains whose people join one named workspace with a named role
- **Public read-only** — whether anonymous visitors browse the default workspace as the shared public viewer
- **Agentless claim expiry** — how long a file claim made without an agent session stays held, 24 hours unless set
- **Storage quota** — how much attachment storage each workspace may use, 1 GiB unless set
