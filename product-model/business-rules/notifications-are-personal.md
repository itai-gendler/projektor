---
appliesTo:
- type: entity
  id: wiki-notification
  effect: reads
permits:
- related: [{verb: receives, entity: user}]
- related: [{verb: receives, entity: user}, {verb: connects, entity: ai-agent}]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki-watchers.ts#listWikiNotifications
---

# A person reads and marks only their own watch notifications

Watch notifications are listed and marked read only for the person they were sent to.
