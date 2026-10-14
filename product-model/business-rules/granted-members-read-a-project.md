---
appliesTo:
- type: entity
  id: project
  effect: reads
permits:
- related: [{verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}]
- related: [{verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}, {verb: connects, entity: ai-agent}]
- related: [{verb: contains, entity: issue}, {verb: is shared through, entity: share-link}, {verb: admits, entity: link-visitor}]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/access.ts#visibleProjectPredicate
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/architecture/access-control.mdx
  title: Access control
---

# Only owners, admins and members whose groups are granted a project read it

A project, and the issues, sprints, comments, links and project wiki pages in it, are readable by the workspace's owners and admins and by members one of whose groups holds a grant on it. A link visitor reads the project's name and key on a live share link.
