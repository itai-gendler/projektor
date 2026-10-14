---
availability:
- place: web::workspace
- place: mcp
references:
- kind: code
  role: implementation
  target: apps/api/src/services/files.ts#createLinkAttachment
---

# Attach link

A member with write access attaches a reference to a wiki page, or an external URL, to an issue or a wiki page.
