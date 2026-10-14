---
availability:
- place: mcp
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/file-claims.ts#releaseFiles
---

# Release files

An agent releases the file claims its session holds, path by path or all at once.
