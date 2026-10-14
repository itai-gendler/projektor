---
availability:
- place: web::shared-link
domain: issues
references:
- kind: code
  role: implementation
  target: apps/api/src/services/share.ts#getSharedIssue
- kind: code
  role: implementation
  target: apps/web/src/islands/ShareView.tsx
---

# View shared issue

Someone holding a share link opens it without signing in and reads the issue it shows.
