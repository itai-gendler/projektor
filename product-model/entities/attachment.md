---
references:
- kind: code
  role: implementation
  target: apps/api/src/services/files.ts#recordUpload
- kind: code
  role: implementation
  target: apps/api/src/services/files.ts#createLinkAttachment
---

# Attachment

A file, a reference to a wiki page, or an external link attached to an issue or a wiki page.

## Information kept

- **Kind** — a file, a wiki page reference or a URL
- **File name** — the uploaded file's name, or the link's label
- **Content type** — the file's type
- **Size** — the file's size
- **URL** — the external address of a link
- **Attached at** — when it was attached
