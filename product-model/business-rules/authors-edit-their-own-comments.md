---
appliesTo:
- type: entity
  id: comment
  effect: changes
permits:
- related: [{verb: writes, entity: user}]
- related: [{verb: writes, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: ai-agent, fact: Scope, is: Read and write}
references:
- kind: code
  role: implementation
  target: apps/api/src/services/comments.ts#updateComment
---

# Only a comment's author edits it

Editing a comment's text is for the person who wrote it, or an agent acting for them, whatever anyone's role.
