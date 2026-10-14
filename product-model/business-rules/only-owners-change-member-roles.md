---
appliesTo:
- type: entity
  id: workspace-membership
  effect: changes
  facts: [Role]
permits:
- related: [{verb: admits, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: admits, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- configuredBy: deployment-settings
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#updateMemberRole
---

# Only a workspace's owners change member roles

Changing anyone's workspace role needs the Owner role. The deployment settings also make admin emails owners of every workspace.
