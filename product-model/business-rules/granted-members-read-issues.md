---
appliesTo:
- type: entity
  id: issue
  effect: reads
permits:
- related: [{verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: contains, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}]
- related: [{verb: contains, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}, {verb: connects, entity: ai-agent}]
- related: [{verb: is shared through, entity: share-link}, {verb: admits, entity: link-visitor}]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#getIssue
- kind: code
  role: implementation
  target: apps/api/src/services/share.ts#getSharedIssue
---

# Only owners, admins and members whose groups are granted the project read its issues

An issue is readable by the workspace's owners and admins and by members one of whose groups holds a grant on its project. A link visitor reads the shared fields of the one issue a live share link shows.
