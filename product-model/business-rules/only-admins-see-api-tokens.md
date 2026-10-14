---
appliesTo:
- type: entity
  id: api-token
  effect: reads
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
  target: apps/api/src/services/workspaces.ts#listTokens
---

# Only workspace owners and admins see the workspace's API tokens

The list of API tokens is for workspace owners and admins; it never shows a token's secret.
