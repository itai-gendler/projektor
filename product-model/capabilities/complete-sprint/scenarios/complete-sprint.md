---
kind: primary
routes:
  web: Web app
steps:
- text: The User confirms completing the active sprint
  kind: actor
  actor: user
  entities:
  - {entity: sprint, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::workspace::sprints
- text: The Product marks the sprint completed and shows how many of its issues and story points were done
  kind: product
  actor: user
  entities:
  - {entity: sprint, effect: changes, from: Active, to: Completed, facts: []}
  - {entity: issue, effect: reads, facts: [Ref, Title, Story points]}
  contexts:
    web:
      place: web::workspace::sprints
---

# Complete the active sprint

## Trigger

The sprint's time box ends.

## Outcome

The sprint is completed with a summary; unfinished issues remain planned into it.

## Edge cases

- Unfinished issues are not carried into another sprint.
