---
entities:
- entity: project
  shows: [Name, Key, Description]
  collects: [Name, Key, Description]
entryPoints:
- web: /
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/ProjectList.tsx
---

# Projects

The projects the member can see, with a form to create one.
