---
appliesTo:
- type: entity
  id: custom-field
  facts: [Internal]
- type: capability
  id: view-shared-issue
references:
- kind: code
  role: implementation
  target: apps/api/src/services/share.ts#getSharedIssue
---

# Internal custom fields never appear on share links

A custom field marked internal is shown to members but never on a share link.
