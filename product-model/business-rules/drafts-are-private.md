---
appliesTo:
- type: entity
  id: wiki-draft
  effect: reads
permits:
- related: [{verb: drafts, entity: user}]
- related: [{verb: drafts, entity: user}, {verb: connects, entity: ai-agent}]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki-drafts.ts#getWikiDraft
---

# Only its author sees or discards a page draft

A page draft belongs to the person who wrote it; nobody else reads it, and it changes nothing on the page until they publish.
