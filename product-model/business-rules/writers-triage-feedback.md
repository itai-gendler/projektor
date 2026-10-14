---
appliesTo:
- type: entity
  id: feedback
  effect: changes
permits:
- related: [{verb: receives, entity: feedback-source}, {verb: gathers, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: receives, entity: feedback-source}, {verb: gathers, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: receives, entity: feedback-source}, {verb: gathers, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: receives, entity: feedback-source}, {verb: gathers, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: receives, entity: feedback-source}, {verb: gathers, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}]
  when:
  - {entity: project-grant, fact: Role, is-not: Viewer}
  - {entity: user, fact: Public viewer, is: 'No'}
- related: [{verb: receives, entity: feedback-source}, {verb: gathers, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: project-grant, fact: Role, is-not: Viewer}
  - {entity: ai-agent, fact: Scope, is: Read and write}
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback.ts#updateFeedbackStatus
---

# Only people who can write to a project triage its feedback

Changing feedback's status or converting it into an issue needs the Owner or Admin workspace role, or a Member or Admin grant on the project.
