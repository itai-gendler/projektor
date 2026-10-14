---
availability:
- place: web::workspace
- place: mcp
domain: issues
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#getIssue
---

# View issue

A member opens one issue by ref or id, with its fields, children rollup, links and comments.
