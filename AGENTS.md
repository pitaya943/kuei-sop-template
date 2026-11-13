# AGENTS.md — Project settings (one per repo; edit for the project)

## Project
- Type: code / research
- Repo: <owner/repo>
- Goal: <one sentence: what this project will build or answer>

## Milestones (Kuei approves each one before work starts)
1. <M1: name | done-when>
2. <M2: name | done-when>

## Important decisions (stop and wait for Kuei)
- <example: data model or API interface change>
- <example: security-related logic>
- <example: research hypothesis, experiment design, evaluation metrics>

## Review depth
- Roles: Alex `<drafts the work plan>`, Chief `<reviews the plan>`, Vera `<verification; PASS before @claude review>`, Kuei `<approves done-when and merges>`.
- After Vera PASS, every PR runs @claude review, then Kuei merges. When the Claude quota is exhausted, Kuei may merge without waiting for that @claude review, and it must be recorded.
- Major changes: run interrogate once more before work starts (optional)
- `@claude review` is review only and does not automatically run grill-me; when grill-me is needed, use a `claude.ai/code` session

## Enabled skills (in .claude/skills/)
- grill-me, teach: load and use only in a `claude.ai/code` cloud session (or Kuei's local session); a Projects thread and the GitHub Action (`@claude`) do not count
- <extras this project needs; add none by default>

## Standing rules
- The builder does not grade their own work: builder and reviewer are different model families
- Open only a branch and a PR; only Kuei merges
- Each PR includes a report: what was done, evidence (commands and results), open questions, and decisions needed from Kuei
- Record decisions in docs/decisions.md (question | choice | reason | date)
- At the end of each milestone, write a short summary under docs/milestones/

## Work plan (one page)

Flow: Alex drafts → Chief reviews → Kuei approves each ticket's done-when in the ticket file → independent tickets run in parallel. Do not hand the whole task to one agent to finish in sequence. Done-when lives in the ticket file.
Model: Never Opus. Fix rounds use a stronger model, and if none is stronger keep the same model and record it. Verification uses a different model family.
Source: [docs/work-plan-template.md](docs/work-plan-template.md). The docs file wins.

## Development rules

Kuei decisions 2026-11-11 19:57, 20:10, 20:22 (via Chief). Project paths and commands use `<placeholder>`.

1. **Spec first (SDD)**: The spec is at `<spec path>`. If the spec is unclear, stop and ask in the PR; do not guess.
2. **Write a failing test first, then the implementation** (TDD/BDD).
3. **Every rejection case** asserts three things: the exact status code, the exact error message, and that no data was written (including no partial write).
4. **The server re-validates every field**; do not trust the client. A missing value must not be quietly filled with a default.
5. **System-wide rules start with an item-by-item inventory table**; every row has a spec source, a check location (file:line), and a test name. Table location: `<inventory table path>`.
6. **CI is all green before it counts as done.** CI must not commit automatically. Only bullet-bots commits; the only exception is @claude review: when Kuei asks, Claude may push fix commits directly to the PR branch.
7. **Do not push main, do not force-push, and do not merge.** Do not touch secrets; neither code nor logs print a key. Change only files in this ticket's scope.
8. **Never Opus.**
9. **PR bodies and comments are always in English**: what was done, evidence (commands and results), open questions, and decisions needed from Kuei. Commands: `<test commands>`.

## Budget notes
- Claude Pro quota is tight: alignment, learning, and the @claude review on every PR after Vera PASS
- When the subscription quota runs out, it shows a reset time (for example "5-hour limit reached - resets [time]"), which is not HTTP 429; 429 is an API key or capacity issue
- The GitHub Action (`@claude`) may share the same Pro quota with claude.ai / Claude Code web (inference; not stated officially)
- <other limits for this project>

## Docs

Standing doc rules are only in [docs/README.md](docs/README.md). If this file and `docs/` disagree, docs wins.
