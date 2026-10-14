---
appliesTo:
- type: entity
  id: attachment
  effect: creates
permits:
- related: [{verb: carries, entity: issue}, {verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: carries, entity: issue}, {verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: carries, entity: issue}, {verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: carries, entity: issue}, {verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: carries, entity: issue}, {verb: contains, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}]
  when:
  - {entity: project-grant, fact: Role, is-not: Viewer}
  - {entity: user, fact: Public viewer, is: 'No'}
- related: [{verb: carries, entity: issue}, {verb: contains, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: project-grant, fact: Role, is-not: Viewer}
  - {entity: ai-agent, fact: Scope, is: Read and write}
references:
- kind: code
  role: implementation
  target: apps/api/src/services/files.ts#recordUpload
- kind: code
  role: implementation
  target: apps/api/src/services/files.ts#createLinkAttachment
---

# Only people who can write to an issue's project attach to it

Attaching a file or link to an issue needs the Owner or Admin workspace role, or a Member or Admin grant on its project; for a wiki page, the right to edit the page.
