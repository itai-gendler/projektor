---
entities:
- entity: issue
  shows: [Title, Body, Priority, Assignee, Custom fields]
- entity: project
  shows: [Name, Key]
- entity: share-link
  shows: [Expires at]
- entity: workspace
  shows: [Branding]
entryPoints:
- web: /share/view
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/ShareView.tsx
- kind: code
  role: implementation
  target: apps/api/src/services/share.ts#getSharedIssue
---

# Shared issue

One issue as a share link shows it, branded for its workspace.
