---
availability:
- place: web::workspace
- place: mcp
references:
- kind: code
  role: implementation
  target: apps/api/src/services/files.ts#deleteAttachment
---

# Delete attachment

Someone with write access removes a file or link attached to an issue or a wiki page.
