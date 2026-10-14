---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent deletes a project
  kind: actor
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product deletes the project with its sprints, project wiki pages, grants and every issue in it whatever its state, and frees issues in other projects that sat under them
  kind: product
  actor: ai-agent
  entities:
  - {entity: project, effect: removes, from: Active}
  - {entity: sprint, as: planned-sprint, effect: removes, from: Planned, with: project}
  - {entity: sprint, as: active-sprint, effect: removes, from: Active, with: project}
  - {entity: sprint, as: completed-sprint, effect: removes, from: Completed, with: project}
  - {entity: wiki-page, as: live-wiki-page, effect: removes, from: Live, with: project}
  - {entity: wiki-page, as: trashed-wiki-page, effect: removes, from: Trashed, with: project}
  - {entity: issue, as: backlog-issue, effect: removes, from: Backlog, with: project}
  - {entity: issue, as: to-do-issue, effect: removes, from: To do, with: project}
  - {entity: issue, as: in-progress-issue, effect: removes, from: In progress, with: project}
  - {entity: issue, as: in-review-issue, effect: removes, from: In review, with: project}
  - {entity: issue, as: done-issue, effect: removes, from: Done, with: project}
  - {entity: issue, as: cancelled-issue, effect: removes, from: Cancelled, with: project}
  - {entity: project-grant, effect: removes, with: project}
  contexts:
    agent:
      place: mcp
---

# Delete a project and everything in it

## Trigger

A project was created by mistake or must be erased.

## Outcome

Nothing of the project remains.

## Edge cases

- An archived project is deleted the same way.
