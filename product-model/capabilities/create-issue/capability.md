---
availability:
- place: web::workspace
- place: mcp
domain: issues
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#createIssue
- kind: code
  role: implementation
  target: apps/api/src/services/definition-of-ready.ts#checkDefinitionOfReady
---

# Create issue

A member with write access to a project files an issue there. It gets the next number in the project, starts in the requested or the default status, and its body is checked against the definition of ready.
