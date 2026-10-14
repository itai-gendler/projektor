---
kind: alternative
routes:
  web: Web app
steps:
- text: The User changes the sprint's name, goal or dates
  kind: actor
  actor: user
  entities:
  - {entity: sprint, effect: reads, facts: [Name, Goal, Start date, End date]}
  contexts:
    web:
      place: web::workspace::issues
- text: The Product saves the sprint
  kind: product
  actor: user
  entities:
  - {entity: sprint, effect: changes, facts: [Name, Goal, Start date, End date]}
  contexts:
    web:
      place: web::workspace::issues
---

# Change a sprint's goal and dates

## Trigger

The sprint's plan changes.

## Outcome

The sprint shows the new details.
