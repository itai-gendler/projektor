---
appliesTo:
- type: entity
  id: wiki-watch
  effect: removes
permits:
- related: [{verb: keeps, entity: user}]
- related: [{verb: keeps, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: ai-agent, fact: Scope, is: Read and write}
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki-watchers.ts#unwatchWikiPage
---

# A person watches and unwatches pages only for themselves

Page watches belong to the person who made them.
