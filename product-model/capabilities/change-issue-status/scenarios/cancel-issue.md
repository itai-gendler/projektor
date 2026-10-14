---
kind: alternative
routes:
  web: Web app
steps:
- text: The User sets an issue's status to Cancelled
  kind: actor
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Ref, Title]}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product cancels the issue and releases any lease and file claims still held on it
  kind: product
  actor: user
  entities:
  - {entity: issue, effect: changes, from: To do, to: Cancelled, facts: []}
  - {entity: issue-lease, effect: changes, from: Held, to: Released, facts: [Released at, Release reason]}
  - {entity: file-claim, effect: changes, from: Held, to: Released, facts: [Released at, Release reason]}
  contexts:
    web:
      place: web::workspace::issue
---

# Cancel an issue

## Trigger

Work will not be done.

## Outcome

The issue is cancelled; no completion report is required.

## Edge cases

- Moving an issue out of the backlog straight to Done or Cancelled never stamps it as ready.
