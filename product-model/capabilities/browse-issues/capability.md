---
availability:
- place: web::workspace
- place: mcp
domain: issues
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#listIssues
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#searchIssues
- kind: code
  role: implementation
  target: apps/web/src/islands/IssueList.tsx
---

# Browse issues

A member lists issues in the projects they can see, as a list, a board grouped by status category or a backlog, filtered by status, priority, assignee, labels, type, sprint, parent, custom field or dates, saved as named views, or searched by keyword.
