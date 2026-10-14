---
appliesTo:
- type: entity
  id: api-token
  effect: creates
permits:
- related: [{verb: issues, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: issues, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#createToken
- kind: code
  role: implementation
  target: apps/api/src/middleware/auth.ts#requireInteractiveHuman
---

# Only workspace owners and admins mint API tokens, and only in person

Minting a workspace API token needs the Owner or Admin role and a person's own browser session; an agent's credential cannot mint one.
