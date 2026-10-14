---
entities:
- entity: issue
  shows: [Ref, Title, Type, Priority, Assignee, Labels, Story points, Child rollup]
  collects: [Title, Body, Type, Priority, Assignee, Parent]
- entity: task-status
  shows: [Name, Category]
- entity: sprint
  shows: [Name, Goal, Start date, End date]
  collects: [Name, Goal, Start date, End date]
- entity: project
  shows: [Name, Key]
entryPoints:
- web: /issues
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/IssueList.tsx
- kind: code
  role: implementation
  target: apps/web/src/islands/issue-list/BoardView.tsx
- kind: code
  role: implementation
  target: apps/web/src/islands/issue-list/SprintBannerSection.tsx
---

# Issues

A project's issues as a list, a board grouped by status category, or a backlog, with filters, saved views, search, a form to create an issue and, when filtered to a sprint, that sprint's details.
