---
appliesTo:
- type: entity
  id: issue
  effect: changes
permits:
- related: [{verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: contains, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}]
  when:
  - {entity: project-grant, fact: Role, is-not: Viewer}
  - {entity: user, fact: Public viewer, is: 'No'}
- related: [{verb: contains, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: project-grant, fact: Role, is-not: Viewer}
  - {entity: ai-agent, fact: Scope, is: Read and write}
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#updateIssue
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/architecture/access-control.mdx
  title: Access control
---

# Only people who can write to a project change its issues

Editing, moving, assigning and planning an issue needs the Owner or Admin workspace role, or a Member or Admin grant on its project.
