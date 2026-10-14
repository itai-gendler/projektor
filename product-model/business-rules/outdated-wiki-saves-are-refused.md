---
appliesTo:
- type: capability
  id: edit-wiki-page
- type: entity
  id: wiki-page
  facts: [Content]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#updateWikiPage
---

# A wiki save based on an outdated revision is refused

A save that names the revision it was based on is refused as a conflict when the page has been saved since; a save naming no base revision overwrites.

## Rationale

Two agents editing one page at once must not silently lose a write.
