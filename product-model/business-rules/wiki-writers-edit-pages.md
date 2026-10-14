---
appliesTo:
- type: entity
  id: wiki-page
  effect: changes
  facts: [Title, Slug, Content, Parent page, Type, Status, Tags, Verified at, Verified by]
permits:
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {fact: Project, absent: true}
  - {entity: workspace-membership, fact: Role, is-not: Viewer}
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {fact: Project, absent: true}
  - {entity: workspace-membership, fact: Role, is-not: Viewer}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: scopes, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}]
  when:
  - {entity: project-grant, fact: Role, is-not: Viewer}
  - {entity: user, fact: Public viewer, is: 'No'}
- related: [{verb: scopes, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: project-grant, fact: Role, is-not: Viewer}
  - {entity: ai-agent, fact: Scope, is: Read and write}
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#updateWikiPage
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#verifyWikiPage
---

# Only wiki writers edit or verify a page

Editing or verifying a workspace page needs any workspace role but Viewer; a project page needs the Owner or Admin workspace role, or a Member or Admin grant on the project.
