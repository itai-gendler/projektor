---
availability:
- place: web::workspace
- place: mcp
domain: issues
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#updateIssue
---

# Edit issue

A member with write access changes an issue's title, body, type, priority, labels, parent, story points or custom fields. A changed body is re-checked against the definition of ready.
