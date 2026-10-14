---
entities:
- entity: issue
  shows: [Ref, Title, Priority, Child rollup]
  collects: [Title, Priority]
entryPoints:
- web: /epics
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/EpicList.tsx
---

# Epics

A project's epics with the progress of their children, and a form to create an epic.
