---
availability:
- place: mcp
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#purgeExpiredWikiPages
- kind: code
  role: implementation
  target: apps/api/src/index.ts#scheduled
---

# Purge wiki trash

Pages that have been in the trash for at least 30 days are removed for good, by a workspace owner or admin on demand and by Projektor itself every day.
