---
availability:
- place: web::workspace
- place: mcp
references:
- kind: code
  role: implementation
  target: apps/api/src/services/files.ts#listAttachments
- kind: code
  role: implementation
  target: apps/api/src/services/files.ts#getAttachmentForDownload
---

# Browse attachments

A member lists the attachments of an issue or a wiki page they can see, and downloads files from the web app.
