---
kind: primary
routes:
  link: Share link
steps:
- text: The Link visitor opens a share link
  kind: actor
  actor: link-visitor
  entities:
  - {entity: share-link, effect: reads, facts: []}
  contexts:
    link:
      place: web::shared-link::shared-issue
- text: The link has not expired, its project is not archived and the person who created it can still see the project
  kind: condition
  actor: link-visitor
  entities:
  - {entity: share-link, effect: reads, facts: [Expires at]}
  - {entity: project, effect: reads, facts: []}
  - {entity: user, effect: reads, facts: []}
  contexts:
    link:
      place: web::shared-link::shared-issue
- text: The Product shows the issue's title, body, status, priority, assignee and public custom fields under the workspace's branding
  kind: product
  actor: link-visitor
  entities:
  - {entity: issue, effect: reads, facts: [Title, Body, Priority, Assignee, Custom fields]}
  - {entity: project, effect: reads, facts: [Name, Key]}
  - {entity: workspace, effect: reads, facts: [Branding]}
  contexts:
    link:
      place: web::shared-link::shared-issue
---

# Open a share link

## Trigger

Someone outside the workspace receives a share link.

## Outcome

The Link visitor reads the issue without an account.

## Edge cases

- Custom fields marked internal are never shown.
