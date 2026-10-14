---
entities:
- entity: issue
  shows: [Ref, Title, Body, Type, Priority, Labels, Assignee, Parent, Sprint, Story points, Custom fields, Child rollup, Definition of ready, Needs audit]
  collects: [Title, Body, Type, Priority, Assignee, Story points]
- entity: task-status
  shows: [Name, Category]
- entity: comment
  shows: [Body, Author kind, Posted at, Edited at]
  collects: [Body]
- entity: issue-link
  shows: [Type]
  collects: [Type]
- entity: share-link
  shows: [Expires at]
- entity: attachment
  shows: [Kind, File name, Size, URL, Attached at]
  collects: [File name, URL]
entryPoints:
- web: /issues/view
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/IssueDetail.tsx
- kind: code
  role: implementation
  target: apps/web/src/islands/IssueDetailParts.tsx
---

# Issue

One issue with everything kept about it: fields, children, links, attachments and comments.
