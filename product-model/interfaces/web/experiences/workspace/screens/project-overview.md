---
entities:
- entity: project
  shows: [Name, Key, Description, Archived at]
  collects: [Description]
- entity: issue
  shows: [Ref, Title]
entryPoints:
- web: /projects/view
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/ProjectLanding.tsx
---

# Project overview

One project: its description, recent issues and pages, and its archive control.
