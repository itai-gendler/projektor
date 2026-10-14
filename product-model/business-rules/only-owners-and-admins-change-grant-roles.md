---
appliesTo:
- type: entity
  id: project-grant
  effect: changes
  facts: [Role]
permits:
- related: [{verb: carries, entity: group}, {verb: defines, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: carries, entity: group}, {verb: defines, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: carries, entity: group}, {verb: defines, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: carries, entity: group}, {verb: defines, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
  - {entity: ai-agent, fact: Scope, is: Read and write}
references:
- kind: code
  role: implementation
  target: apps/api/src/services/groups.ts#setGroupGrant
---

# Only workspace owners and admins change a grant's role

Changing the role a group holds on a project needs the Owner or Admin role.
