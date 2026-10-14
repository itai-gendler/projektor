---
id: projektor
summary: A self-hosted issue tracker and wiki that people and AI coding agents run together, with issue leases, file claims and a per-project cap on agent work.
category: project-management
tags:
- issue-tracker
- wiki
- mcp
- ai-agents
- self-hosted
authors:
- name: TAJD
  url: https://github.com/TAJD
license: MIT
languages:
- en
limitations:
- People sign in through the Cloudflare Access application the operator puts in front of the deployment; Projektor keeps no passwords of its own.
- A project is visible to an ordinary member only once an owner or admin grants it to one of their groups; workspace membership alone shows no projects.
- File claims match exact path strings; claiming a folder or a pattern reserves nothing beneath it.
- API tokens and connected applications are created and withdrawn only from a person's own browser session, never by an agent.
- Each deployment runs in the operator's own Cloudflare account; there is no hosted service.
references:
- kind: doc
  role: intent
  target: README.md
  title: README
- kind: doc
  role: context
  target: llms.txt
  title: Agent quick reference
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/philosophy/design-principles.md
  title: Design principles
---

# Projektor

Projektor is an issue tracker and wiki that an AI coding agent runs as well as a person does. Workspaces hold projects; projects hold issues, sprints and project wiki pages; the workspace keeps its own wiki pages too. People work in a web app with list, board and backlog views, sprints, a nested wiki and flow metrics. Agents reach the same data through an MCP server, where they also register sessions, lease issues, claim the files they will edit and message each other, so that several agents can work one workspace at once without double-working a ticket or editing the same file. Access is decided per workspace role and per project through group grants.

## Intent

The project describes itself as "AI-native project management, self-hosted on Cloudflare": the agent files the ticket, moves it and writes the page instead of asking a person to. Coordination lives in the work graph: issue leases and file claims sit beside the tickets, contention is kept as data, and the tracker enforces a work-in-progress cap on agents because agents make WIP inflation free. People still run the project: backlog, board, epics, sprints, a wiki and flow metrics, in a normal web app.
