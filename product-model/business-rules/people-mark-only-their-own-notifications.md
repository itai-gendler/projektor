---
appliesTo:
- type: entity
  id: wiki-notification
  effect: changes
permits:
- related: [{verb: receives, entity: user}]
- related: [{verb: receives, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: ai-agent, fact: Scope, is: Read and write}
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki-watchers.ts#markWikiNotificationsRead
---

# Only the person a watch notification was sent to marks it read

Marking a watch notification read is for the person it was sent to.
