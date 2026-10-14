---
entities:
- entity: sprint
  shows: [Name, Goal, Start date, End date]
  collects: [Name, Goal, Start date, End date]
- entity: issue
  shows: [Ref, Title, Story points]
entryPoints:
- web: /sprints
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/SprintManager.tsx
---

# Sprints

A project's sprints with their dates, goals and completed story points, and a form to create one.
