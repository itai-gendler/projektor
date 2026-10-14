---
availability:
- place: web::workspace
domain: issues
references:
- kind: code
  role: implementation
  target: apps/api/src/services/share.ts#createShareToken
- kind: code
  role: implementation
  target: apps/web/src/islands/IssueDetailParts.tsx
---

# Share issue

A member with write access to the issue's project creates a public link that shows the issue read-only to anyone holding it for three days.
