---
availability:
- place: web::workspace
- place: mcp
domain: issues
references:
- kind: code
  role: implementation
  target: apps/api/src/services/comments.ts#deleteComment
---

# Delete comment

The author of a comment, or a workspace owner or admin, deletes it.
