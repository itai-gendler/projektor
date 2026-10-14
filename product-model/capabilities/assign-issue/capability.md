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

# Assign issue

A member with write access assigns an issue to a workspace member, replacing any earlier assignee.
