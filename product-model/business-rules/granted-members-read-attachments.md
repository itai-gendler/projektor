---
appliesTo:
- type: entity
  id: attachment
  effect: reads
permits:
- related: [{verb: carries, entity: issue}, {verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: carries, entity: issue}, {verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: carries, entity: issue}, {verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: carries, entity: issue}, {verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: carries, entity: issue}, {verb: contains, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}]
- related: [{verb: carries, entity: issue}, {verb: contains, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}, {verb: connects, entity: ai-agent}]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/files.ts#listAttachments
---

# Only those who can see what an attachment hangs on read it

An attachment, its metadata and its bytes, is readable only by those who can read the issue or wiki page it is attached to.
