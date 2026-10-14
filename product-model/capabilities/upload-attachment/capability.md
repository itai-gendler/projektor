---
availability:
- place: web::workspace
references:
- kind: code
  role: implementation
  target: apps/api/src/services/files.ts#recordUpload
- kind: doc
  role: context
  target: apps/docs/src/content/docs/agents/rest-endpoints.md
  title: REST endpoints
- kind: code
  role: implementation
  target: apps/api/src/services/files.ts#assertUploadAllowed
---

# Upload attachment

A member with write access attaches a file to an issue or a wiki page, within the size, type and workspace storage limits.
