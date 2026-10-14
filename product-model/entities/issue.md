---
domain: issues
relations:
- entity: comment
  verb: has
  cardinality: one-to-many
- entity: issue-lease
  verb: is leased through
  cardinality: one-to-many
- entity: file-claim
  verb: covers
  cardinality: one-to-many
- entity: share-link
  verb: is shared through
  cardinality: one-to-many
- entity: issue-link
  verb: starts
  cardinality: one-to-many
- entity: issue-link
  verb: ends
  cardinality: one-to-many
- entity: issue
  verb: parents
  cardinality: one-to-many
- entity: attachment
  verb: carries
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#createIssue
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#updateIssue
- kind: code
  role: implementation
  target: apps/api/src/services/task-statuses.ts#seedDefaultTaskStatuses
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/agents/workflow-spec.md
  title: Workflow spec
---

# Issue

A unit of work in a project, the thing people and agents file, pick up, move and close. Its state is its task status: every workspace status falls into one of the states below by its category and by whether it is the backlog or a review step, and a new workspace's statuses are exactly these six. An epic is an issue of the Epic type whose children sit under it.

## Information kept

- **Ref** — the project key and a number allocated in order within the project, such as PROJ-42
- **Title** — a one-line summary
- **Body** — the markdown description
- **Type** — the task type, such as Epic, Story, Task or Bug
- **Priority** — Urgent, High, Medium, Low or None
- **Labels** — up to 20 exact-match tags
- **Assignee** — the workspace member it is assigned to
- **Parent** — the issue it sits under, at most five levels deep
- **Sprint** — the sprint it is planned into
- **Story points** — the estimate kept in the default story points custom field
- **Custom fields** — values for the workspace's custom field definitions
- **Definition of ready** — whether the body states acceptance criteria and a scope of files, and which is missing
- **Completion report** — the summary, verification and optional pull request link filed when work was handed in
- **Needs audit** — set when an agent closed it with evidence nothing external can check
- **Author kind** — whether a person or an agent created it
- **Ready at** — when it first left the backlog for open work
- **Started at** — when it first entered an in-progress or review status
- **In review at** — when it first entered a review step
- **Done at** — when it first reached a done status
- **Review bounces** — how many times it left review for more work
- **Child rollup** — counts of its visible children by state

## States

### Backlog

Not yet triaged into a workable slice; the default status of a new workspace.

### To do

Triaged and open for work but not started.

### In progress

Being worked.

### In review

Handed in by the implementer and waiting for review; a review-step status.

### Done

Finished.

### Cancelled

Will not be done.
