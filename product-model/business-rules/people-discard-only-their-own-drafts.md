---
appliesTo:
- type: entity
  id: wiki-draft
  effect: removes
permits:
- related: [{verb: drafts, entity: user}]
- related: [{verb: drafts, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: ai-agent, fact: Scope, is: Read and write}
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki-drafts.ts#discardWikiDraft
---

# Only a draft's author discards it

Discarding a page draft is for the person who wrote it.
