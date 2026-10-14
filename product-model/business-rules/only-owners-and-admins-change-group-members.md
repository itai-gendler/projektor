---
appliesTo:
- type: entity
  id: group
  effect: changes
  facts: [Members]
permits:
- related: [{verb: defines, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: defines, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: defines, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: defines, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- configuredBy: deployment-settings
references:
- kind: code
  role: implementation
  target: apps/api/src/services/groups.ts#addGroupMember
- kind: code
  role: implementation
  target: apps/api/src/services/provisioning.ts#provisionPublicViewer
---

# Only workspace owners and admins change who is in a group

Adding or removing a group's members needs the Owner or Admin role. The deployment settings put the anonymous public viewer in the Public viewers group.
