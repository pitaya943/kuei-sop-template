# AGENTS.md — Project settings (one per repo; edit for the project)

## Project
- Type: code / research
- Repo: <owner/repo>
- Goal: <one sentence: what this project will build or answer>

## Milestones
Cut milestones in [docs/milestones/README.md](docs/milestones/README.md). Kuei approves them before the work plan.

## Important decisions (stop and wait for Kuei)
- <example: data model or API interface change>
- <example: security-related logic>
- <example: research hypothesis, experiment design, evaluation metrics>

## Review depth
- `@claude` review and the quota exception: [docs/claude-review.md](docs/claude-review.md).

## Enabled skills (in .claude/skills/)
- grill-me, teach (where they run: [docs/claude-review.md](docs/claude-review.md))
- <extras this project needs; add none by default>

## Standing rules
- The builder does not grade their own work: builder and reviewer are different model families
- Handoff fields: From line, model, ticket path and milestone, agent URL, what was done, evidence, open questions, and decisions needed from Kuei
- Name the model in the commit trailer, the PR body, and comments.
- Record decisions in docs/decisions.md (question | choice | reason | date)
- One pull request per milestone: [docs/milestones/README.md](docs/milestones/README.md)

## Work plan
One page for the current milestone only: [docs/work-plan-template.md](docs/work-plan-template.md).

## Development rules

Kuei decisions 2026-11-11 19:57, 20:10, 20:22 (via Chief). Project paths and commands use `<placeholder>`.

1. **Spec first (SDD)**: The spec is at `<spec path>`. If the spec is unclear, stop and ask in the PR; do not guess.
2. **Write a failing test first, then the implementation** (TDD/BDD).
3. **Every rejection case** asserts three things: the exact status code, the exact error message, and that no data was written (including no partial write).
4. **The server re-validates every field**; do not trust the client. A missing value must not be quietly filled with a default.
5. **System-wide rules start with an item-by-item inventory table**; every row has a spec source, a check location (file:line), and a test name. Table location: `<inventory table path>`.
6. **CI is all green before it counts as done.** CI must not commit automatically. Only bullet-bots commits; the only exception is @claude review: when Kuei asks, Claude may push fix commits directly to the PR branch.
7. **Do not push main, do not force-push, and do not merge; only Kuei merges.** Do not touch secrets; neither code nor logs print a key. Change only files in this ticket's scope.
8. **Never Opus.**
9. **PR bodies and comments are always in English** and include the handoff fields listed under Standing rules. Commands: `<test commands>`.

## Docs

Standing doc rules are only in [docs/README.md](docs/README.md). If this file and `docs/` disagree, docs wins.
