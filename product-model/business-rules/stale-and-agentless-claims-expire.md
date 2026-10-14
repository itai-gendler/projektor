---
appliesTo:
- type: capability
  id: claim-files
- type: entity
  id: deployment-settings
references:
- kind: code
  role: implementation
  target: apps/api/src/services/file-claims.ts#claimFiles
- kind: code
  role: implementation
  target: apps/api/src/services/file-claims.ts#parseFileClaimTtlSeconds
---

# A file claim lapses when its session goes quiet, or after the expiry when it has no session

A claim held by a session silent for more than 120 seconds is released as expired when someone claims the path. A claim made without any session is released the same way once it is older than the deployment's agentless claim expiry, 24 hours unless set. Neither is recorded as a conflict.
