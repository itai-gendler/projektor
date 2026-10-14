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

# Unassign issue

A member with write access clears an issue's assignee.
