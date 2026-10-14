---
entities:
- entity: issue
  shows: [Ref, Title, Priority, Assignee]
entryPoints:
- web: /my-issues
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/MyIssues.tsx
---

# My Issues

The issues assigned to the signed-in member across the projects they can see.
