---
kind: primary
routes:
  web: Web app
steps:
- text: The User sets a reviewed issue's status to Done
  kind: actor
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Ref, Title]}
  contexts:
    web:
      place: web::workspace::issue
- text: No agent has ever leased the issue, or a completion report is already on file
  kind: condition
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Completion report]}
  - {entity: issue-lease, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product closes the issue, stamps when it was done and releases any lease and file claims still held on it
  kind: product
  actor: user
  entities:
  - {entity: issue, effect: changes, from: In review, to: Done, facts: [Done at]}
  - {entity: issue-lease, effect: changes, from: Held, to: Released, facts: [Released at, Release reason]}
  - {entity: file-claim, effect: changes, from: Held, to: Released, facts: [Released at, Release reason]}
  contexts:
    web:
      place: web::workspace::issue
---

# Close a reviewed issue

## Trigger

Review is over and the work is accepted.

## Outcome

The issue is done and no longer blocks other agents.
