---
domain: issues
references:
- kind: code
  role: implementation
  target: apps/api/src/services/comments.ts#addComment
---

# Comment

A comment on an issue. Completion reports are recorded as comments too.

## Information kept

- **Body** — the markdown text
- **Author kind** — whether a person or an agent wrote it
- **Posted at** — when it was posted
- **Edited at** — when it was last edited
