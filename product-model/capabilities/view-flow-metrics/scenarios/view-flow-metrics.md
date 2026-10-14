---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens the metrics for a time window
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::metrics
- text: The Product computes the project's flow from the times its issues first became ready, started, entered review and were done, and from how its leases ended
  kind: product
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Ready at, Started at, In review at, Done at, Review bounces]}
  - {entity: issue-lease, effect: reads, facts: [Release reason]}
  - {entity: project, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::metrics
---

# Read a project's flow

## Trigger

The User wants to know whether the agent WIP limit is about right.

## Outcome

The User sees how work flows through the project.

## Edge cases

- Cycle time starts when an issue first enters an in-progress or review status, not when an agent leases it.
