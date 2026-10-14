---
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#listWikiRevisions
---

# Page revision

A saved earlier version of a wiki page's content, kept each time the content changes.

## Information kept

- **Content** — the page content as it was
- **Title** — the page title as it was
- **Summary** — the editor's optional note on the change
- **Author** — who made the change
- **Saved at** — when the change was made
