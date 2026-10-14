---
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki-watchers.ts#notifyWikiWatchers
- kind: code
  role: implementation
  target: apps/api/src/services/wiki-watchers.ts#listWikiNotifications
---

# Watch notification

A note to one person that a page they watch was created beneath it, changed, verified, restored or deleted. It keeps the page's title and slug so it still makes sense after the page is gone.

## Information kept

- **Page title** — the page's title at the time
- **Page slug** — the page's slug at the time
- **Action** — created, updated or deleted
- **Notified at** — when it was made

## States

### Unread

Not yet marked read.

### Read

Marked read.
