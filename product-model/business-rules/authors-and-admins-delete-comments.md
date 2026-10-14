---
appliesTo:
- type: entity
  id: comment
  effect: removes
permits:
- related: [{verb: writes, entity: user}]
- related: [{verb: writes, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: has, entity: issue}, {verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: has, entity: issue}, {verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: has, entity: issue}, {verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: has, entity: issue}, {verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
  - {entity: ai-agent, fact: Scope, is: Read and write}
references:
- kind: code
  role: implementation
  target: apps/api/src/services/comments.ts#deleteComment
---

# Only a comment's author or a workspace owner or admin deletes it

Deleting a comment is for its author, or for the workspace's owners and admins.
