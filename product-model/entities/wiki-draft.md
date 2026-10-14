---
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki-drafts.ts#saveWikiDraft
---

# Page draft

A person's unsaved edit of a wiki page, kept on the server so it survives a device switch. Each person has at most one draft per page, visible only to them, and it is not a revision.

## Information kept

- **Title** — the draft title
- **Content** — the draft content
- **Base revision** — the page revision the draft started from
- **Saved at** — when it was last saved
