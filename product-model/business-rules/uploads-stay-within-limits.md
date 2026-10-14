---
appliesTo:
- type: capability
  id: upload-attachment
- type: entity
  id: deployment-settings
  facts: [Storage quota]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/files.ts#assertUploadAllowed
---

# An upload is at most 50 MB, of an allowed type, and within the workspace's storage quota

Files over 50 MB, of types that are not allowed, or that would take the workspace past its storage quota, 1 GiB unless the deployment sets another, are refused.
