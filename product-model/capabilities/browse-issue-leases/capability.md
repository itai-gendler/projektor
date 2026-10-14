---
availability:
- place: mcp
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issue-leases.ts#listIssueLeases
---

# Browse issue leases

An agent lists the live issue leases in the projects it can see, optionally by issue, session or project, or including leases whose session has gone quiet.
