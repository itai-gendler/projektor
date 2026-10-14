---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent marks the page as verified
  kind: actor
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: reads, facts: [Freshness]}
  contexts:
    agent:
      place: mcp
- text: The Product stamps the page's frontmatter with now and the signed-in person's email, saving the replaced content as a revision
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: changes, facts: [Verified at, Verified by, Content]}
  - {entity: wiki-revision, effect: creates, facts: [Content, Title, Author, Saved at]}
  contexts:
    agent:
      place: mcp
---

# Vouch for a page through MCP

## Trigger

The AI agent has checked that a page still holds.

## Outcome

The page is fresh again until its interval next elapses.

## Edge cases

- The verifier is always the signed-in person; an agent cannot name someone else.
