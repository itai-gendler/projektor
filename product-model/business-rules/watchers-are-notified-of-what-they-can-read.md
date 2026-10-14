---
appliesTo:
- type: capability
  id: edit-wiki-page
- type: entity
  id: wiki-notification
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki-watchers.ts#notifyWikiWatchers
---

# Watchers hear about changes only to pages they can still read, and never about their own

A change to a page notifies every watcher of the page, and every watcher of a page above it whose watch covers its subtree, who can still read the page; the person who made the change is not notified.
