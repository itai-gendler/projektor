---
availability:
- place: mcp
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki-links.ts#listBrokenWikiLinks
---

# Browse broken wiki links

A member lists links whose target title or address matched no page, as a maintenance queue. A broken link resolves by itself once a matching page is created.
