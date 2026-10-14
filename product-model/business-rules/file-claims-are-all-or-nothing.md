---
appliesTo:
- type: capability
  id: claim-files
- type: entity
  id: file-claim
  effect: changes
  to: Released
references:
- kind: code
  role: implementation
  target: apps/api/src/services/file-claims.ts#claimFiles
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/philosophy/coordination-model.md
  title: Coordination model
---

# A file claim succeeds for every path or for none

If any requested path is held by a live claim and the caller does not force it, nothing is claimed. A forced claim releases the holders as overridden and messages both issues' channels; it cannot override a holder whose issue the claimer cannot see.
