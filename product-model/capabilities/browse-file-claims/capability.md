---
availability:
- place: mcp
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/file-claims.ts#listFileClaims
---

# Browse file claims

An agent lists the live file claims in the workspace, optionally by issue, path or project, or including claims whose holder has gone quiet or whose agentless claim has expired.
