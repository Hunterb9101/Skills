---
name: publish-issue
description: Formalize rough issue ideas into concise, actionable GitHub issue tickets and optionally publish them. Use when the user has a vague bug, feature request, refactor, technical debt item, or follow-up task and wants it shaped for later execution by an AI agent or human contributor.
---

# Publish Issue

## Overview

Turn an informal issue idea into a ticket with clear context, acceptance criteria, and enough implementation orientation for a future agent to act without rediscovering the problem. Draft first, then publish only after the user confirms the final title, body, repository, and labels/assignees when applicable.

## Workflow

1. Clarify the repo and issue type.
   - Identify the target repository before publishing.
   - Classify as `bug`, `feature`, `refactor`, `technical debt`, `documentation`, `research`, or `experiment`.
   - Align on the problem before drafting. Ask focused clarification questions until the problem, scope, and desired outcome are clear enough that the ticket would not misrepresent the user's intent.
   - Batch questions when multiple answers are needed, and explain why each question matters.

   Classification definitions:
   - `bug`: Existing intended behavior is broken, incorrect, unstable, or regressed.
   - `feature`: New user-visible or API-visible capability that does not exist yet.
   - `refactor`: Internal code structure change that should preserve external behavior.
   - `technical debt`: Maintenance, reliability, performance, test, or architecture work needed to reduce future cost or risk.
   - `documentation`: README, docs, examples, comments, or usage guidance are missing, stale, unclear, or misleading.
   - `research`: Investigation needed before deciding whether or how to implement a change.
   - `experiment`: Empirical trial with defined inputs, evaluation criteria, and expected output, often for model, product, or performance comparison.

2. Gather minimal evidence.
   - Use local files, logs, test output, GitHub context, or user notes when available.
   - Prefer concrete references: stable GitHub links, commands, versions, observed behavior, metrics, screenshots, or related tickets.
   - Convert local file references into GitHub permalinks before publishing whenever the repository and commit or branch are known.
   - Do not invent impact, root cause, labels, assignees, milestones, or implementation details.

3. Draft the ticket.
   - Keep the title specific, searchable, and outcome-oriented.
   - Write the body in the smallest template that fits the issue.
   - Make acceptance criteria observable and testable.
   - Include non-goals when they prevent scope creep.

4. Review before publishing.
   - Present the exact title and body.
   - State the repository and any labels, assignees, or milestone.
   - Ask for confirmation before creating the GitHub issue unless the user explicitly already asked to publish a specific final draft.

5. Publish and report.
   - Create the issue with the GitHub connector when available.
   - Return the issue number/link and a one-sentence summary of what was filed.

## Ticket Standard

### Title

Use an imperative or outcome phrase that names the affected area and desired result.

Good:
- `Add grouped stratified CV support for binary classifiers`
- `Fix MLflow metric logging for repeated CV runs`
- `Document categorical feature handling in LightGBMModel`

Avoid:
- `CV`
- `Bug`
- `Improve model stuff`

### Problem

Describe the gap, failure, or opportunity in one to three short paragraphs. Name what is happening now and why that is insufficient.

Good problem statements:
- Say who or what is blocked.
- Include the observed behavior or missing capability.
- Avoid diagnosing root cause unless supported by evidence.

### Context

Give the future agent enough orientation to start in the right place.

Include whichever details are relevant:
- Repository, package, module, or stable GitHub file links.
- Commands, configs, versions, dependency names, branches, or environment.
- Error messages, failing tests, metrics, screenshots, or logs.
- Related issues, PRs, experiments, notebooks, or user notes.

### Proposed Direction

Offer a likely path without over-constraining the implementer. Mark uncertain ideas as suggestions.

Use this section to:
- Point to an existing pattern or abstraction.
- Explain a preferred API shape.
- Mention compatibility, migration, performance, or design constraints.
- State when investigation is needed before implementation.

### Acceptance Criteria

Write completion checks as verifiable outcomes.

Good criteria:
- `A regression test covers the failing case.`
- `The helper preserves row alignment between input data and OOF predictions.`
- `The public API is documented with a minimal usage example.`
- `Existing callers continue to pass without migration.`

Avoid criteria that cannot be checked:
- `Code is better.`
- `Make it robust.`
- `Improve UX.`

### Notes

Add references that are useful but not required for the main flow. Keep this section short. Move design docs, long logs, or large traces into linked artifacts when possible.

## Templates

### Generic

```md
## Problem

...

## Context

...

## Proposed Direction

...

## Acceptance Criteria

- ...

## Notes

...
```

### Bug

```md
## Bug

...

## Steps To Reproduce

1. ...
2. ...
3. ...

## Expected Behavior

...

## Actual Behavior

...

## Environment

...

## Acceptance Criteria

- ...
```

### Research Or Experiment

```md
## Question

...

## Context

...

## Investigation Plan

...

## Decision Criteria

- ...

## Output

- ...
```

## Publishing Rules

- Confirm before publishing when the draft was created in the same turn.
- Never publish to an ambiguous repository.
- Do not apply labels, milestones, or assignees unless the user requested them or they are clearly established by repo convention.
- If the issue body depends on local code evidence, use stable GitHub links to files, lines, commits, PRs, or issues. Use local paths only in drafts or when no GitHub source is available.
- Prefer explicit acceptance criteria and source references over broad implementation prose.
