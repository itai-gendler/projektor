---
kind: primary
routes:
  web: Web app
steps:
- text: The User marks the page as verified
  kind: actor
  actor: user
  entities:
  - {entity: wiki-page, effect: reads, facts: [Freshness]}
  contexts:
    web:
      place: web::workspace::wiki-page
- text: The Product stamps the page's frontmatter with now and the signed-in person's email, saving the replaced content as a revision
  kind: product
  actor: user
  entities:
  - {entity: wiki-page, effect: changes, facts: [Verified at, Verified by, Content]}
  - {entity: wiki-revision, effect: creates, facts: [Content, Title, Author, Saved at]}
  contexts:
    web:
      place: web::workspace::wiki-page
---

# Vouch for a page

## Trigger

The User has checked that a page still holds.

## Outcome

The page is fresh again until its interval next elapses.

## Edge cases

- The verifier is always the signed-in person; an agent cannot name someone else.
