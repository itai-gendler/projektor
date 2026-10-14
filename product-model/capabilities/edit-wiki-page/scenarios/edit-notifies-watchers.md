---
kind: alternative
routes:
  web: Web app
steps:
- text: The User saves a change to a page others watch
  kind: actor
  actor: user
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title, Content]}
  contexts:
    web:
      place: web::workspace::wiki-page
- text: The Product keeps the previous content as a page revision and saves the page
  kind: product
  actor: user
  entities:
  - {entity: wiki-revision, effect: creates, facts: [Content, Title, Author, Saved at]}
  - {entity: wiki-page, effect: changes, facts: [Content]}
  contexts:
    web:
      place: web::workspace::wiki-page
- text: The Product sends a watch notification to every watcher of the page or of a page above it whose watch covers its subtree, except the User
  kind: product
  actor: user
  entities:
  - {entity: wiki-watch, effect: reads, facts: [Include subtree]}
  - {entity: wiki-notification, effect: creates, to: Unread, facts: [Page title, Page slug, Action, Notified at]}
  contexts:
    web:
      place: web::workspace::wiki-page
---

# Editing a watched page notifies its watchers

## Trigger

A page several people follow changes.

## Outcome

Each watcher who can still read the page has an unread notification.
