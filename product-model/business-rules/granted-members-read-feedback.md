---
appliesTo:
- type: entity
  id: feedback
  effect: reads
permits:
- related: [{verb: receives, entity: feedback-source}, {verb: gathers, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: receives, entity: feedback-source}, {verb: gathers, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: receives, entity: feedback-source}, {verb: gathers, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: receives, entity: feedback-source}, {verb: gathers, entity: project}, {verb: contains, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: receives, entity: feedback-source}, {verb: gathers, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}]
- related: [{verb: receives, entity: feedback-source}, {verb: gathers, entity: project}, {verb: receives, entity: project-grant}, {verb: carries, entity: group}, {verb: includes, entity: user}, {verb: connects, entity: ai-agent}]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback.ts#listFeedback
---

# Only those who can see a project read its feedback

Feedback is readable by the workspace's owners and admins and by members whose groups are granted its project.
