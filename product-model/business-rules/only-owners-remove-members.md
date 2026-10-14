---
appliesTo:
- type: entity
  id: workspace-membership
  effect: removes
permits:
- related: [{verb: admits, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: admits, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
  - {entity: ai-agent, fact: Scope, is: Read and write}
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#removeMember
---

# Only a workspace's owners remove members

Removing a member needs the Owner role, and an owner never removes themselves.
