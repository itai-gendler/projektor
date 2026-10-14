---
appliesTo:
- type: entity
  id: wiki-page
  facts: [Trashed at]
- type: capability
  id: purge-wiki-trash
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#purgeExpiredWikiPages
---

# A trashed page is kept for 30 days

A page in the trash can be restored for 30 days; after that it is purged with its revisions and attachments.
