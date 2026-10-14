---
entities:
- entity: wiki-page
  shows: [Title, Slug, Content, Parent page, Project, Type, Status, Tags, Verified at, Verified by, Freshness]
  collects: [Title, Content]
- entity: wiki-revision
  shows: [Content, Title, Summary, Author, Saved at]
- entity: attachment
  shows: [Kind, File name, Size, URL, Attached at]
  collects: [File name, URL]
- entity: wiki-draft
  shows: [Content, Saved at]
entryPoints:
- web: /wiki/view
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/WikiPage.tsx
---

# Wiki page

One wiki page: its rendered content, editor, verification and revision history.
