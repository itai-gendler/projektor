---
availability:
- place: mcp
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/file-claims.ts#claimFiles
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/philosophy/coordination-model.md
  title: Coordination model
---

# Claim files

An agent claims exact file paths for an issue before editing them. The claim is all or nothing: if a live claim holds any path, nothing is claimed unless the caller forces it. Every contended path is recorded.
