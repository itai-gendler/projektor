---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent closes an issue with a completion report that names work left undone
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, as: closed-issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product closes the issue and files a follow-up issue under the same parent with the same labels, linked as following from it
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, as: closed-issue, effect: changes, from: In progress, to: Done, facts: [Completion report, Done at]}
  - {entity: issue, as: follow-up, effect: creates, to: Backlog, facts: [Ref, Title, Body, Labels, Parent]}
  - {entity: issue-link, effect: creates, facts: [Type], with: follow-up}
  contexts:
    agent:
      place: mcp
---

# Closing with a remainder files a follow-up

## Trigger

An agent finished most of an issue but not all of it.

## Outcome

The remainder is tracked as its own issue and its ref is returned.

## Edge cases

- If the follow-up cannot be created the close still stands and the answer says to file it by hand.
