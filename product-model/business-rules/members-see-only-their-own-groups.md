---
appliesTo:
- type: entity
  id: group
  effect: reads
permits:
- related: [{verb: defines, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: defines, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: defines, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: defines, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: includes, entity: user}]
- related: [{verb: includes, entity: user}, {verb: connects, entity: ai-agent}]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/groups.ts#listGroups
- kind: code
  role: implementation
  target: apps/api/src/services/groups.ts#getGroup
---

# Owners and admins see every group; other members see only their own

Listing groups and their grants shows owners and admins every group in the workspace, and every other member only the groups they belong to.
