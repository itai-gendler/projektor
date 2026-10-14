---
availability:
- place: mcp
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#getWikiBacklinks
---

# View backlinks

A member lists the pages that link to a page, by title link or by its address, each with the citing text. Backlinks survive renames.
