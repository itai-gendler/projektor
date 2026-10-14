---
appliesTo:
- type: entity
  id: wiki-page
  effect: reads
permits:
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {fact: Project, absent: true}
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {fact: Project, absent: true}
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: scopes, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}]
- related: [{verb: scopes, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}, {verb: connects, entity: ai-agent}]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#getWikiPage
---

# Workspace pages are readable by every member; project pages only by those who can see the project

A page with no project is readable by every member of its workspace. A project page is readable by the workspace's owners and admins and by members whose groups are granted the project.
