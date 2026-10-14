---
appliesTo:
- type: entity
  id: share-link
  effect: creates
permits:
- related: [{verb: is shared through, entity: issue}, {verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: is shared through, entity: issue}, {verb: contains, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: is shared through, entity: issue}, {verb: contains, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}]
  when:
  - {entity: project-grant, fact: Role, is-not: Viewer}
  - {entity: user, fact: Public viewer, is: 'No'}
references:
- kind: code
  role: implementation
  target: apps/api/src/services/share.ts#createShareToken
---

# Only people who can write to an issue's project share it

Creating a share link needs the Owner or Admin workspace role, or a Member or Admin grant on the issue's project.
