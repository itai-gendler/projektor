---
appliesTo:
- type: capability
  id: view-shared-issue
- type: entity
  id: share-link
references:
- kind: code
  role: implementation
  target: apps/api/src/services/share.ts#getSharedIssue
---

# A share link shows its issue for three days, while its creator can still see it

A share link stops resolving after three days, when its issue is deleted, when its project is archived, or when the person who created it can no longer read the project. Internal custom fields are never shown.

## Rationale

A public link must never outlive the access of the person who chose to publish it.
