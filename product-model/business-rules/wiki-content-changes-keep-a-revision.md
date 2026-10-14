---
appliesTo:
- type: capability
  id: edit-wiki-page
- type: entity
  id: wiki-revision
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#updateWikiPage
---

# Every change to a page's content keeps the previous content as a revision

Each save that changes a page's content, including a verification stamp and a section patch, first keeps the content it replaces as a page revision.
