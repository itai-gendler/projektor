---
domain: wiki
relations:
- entity: wiki-revision
  verb: records
  cardinality: one-to-many
- entity: wiki-page
  verb: parents
  cardinality: one-to-many
- entity: attachment
  verb: carries
  cardinality: one-to-many
- entity: wiki-draft
  verb: has
  cardinality: one-to-many
- entity: wiki-watch
  verb: is watched through
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#createWikiPage
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#updateWikiPage
---

# Wiki page

A markdown page in the wiki. A page with no project is a workspace page every member sees; a page with a project follows that project's visibility. Pages nest under parent pages, link to each other by title or slug, and may carry frontmatter that declares a type, status, tags and how often the page must be re-verified.

## Information kept

- **Title** — the page title
- **Slug** — the unique address; old slugs keep redirecting after a rename
- **Content** — the markdown body, frontmatter included
- **Parent page** — the page it sits under
- **Project** — the project it belongs to; absent for a workspace page
- **Type** — the frontmatter type, such as runbook, adr, spec or note
- **Status** — the frontmatter status, such as draft or stale
- **Tags** — frontmatter tags
- **Template** — whether it is offered as a template for new pages
- **Verified at** — when someone last vouched for it
- **Verified by** — the email of who last vouched for it
- **Freshness** — whether its declared verify interval has elapsed since it was verified
- **Trashed at** — when it was moved to the trash

## States

### Live

Readable, searchable and linkable.

### Trashed

In the trash for 30 days, restorable until it is purged.
