---
appliesTo:
- type: entity
  id: feedback-source
  effect: creates
permits:
- related: [{verb: gathers, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: gathers, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: gathers, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: gathers, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
  - {entity: ai-agent, fact: Scope, is: Read and write}
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback-sources.ts#createFeedbackSource
---

# Only workspace owners and admins create feedback sources

Creating a feedback source needs the Owner or Admin workspace role.
