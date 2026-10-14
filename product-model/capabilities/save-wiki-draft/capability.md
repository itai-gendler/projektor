---
availability:
- place: web::workspace
- place: mcp
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki-drafts.ts#saveWikiDraft
---

# Save wiki draft

While a member edits a page, their unsaved changes are kept as their own server-side draft, one per page, so they survive a device switch.
