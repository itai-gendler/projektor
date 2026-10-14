---
appliesTo:
- type: capability
  id: claim-files
- type: entity
  id: file-claim
  facts: [Path]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/file-claims.ts#claimFiles
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/philosophy/coordination-model.md
  title: Coordination model
---

# File claims match exact path strings

Two claims conflict only when they name the same path string; a folder or a pattern reserves nothing beneath it.
