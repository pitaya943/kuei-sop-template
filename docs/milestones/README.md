# Milestones

Kuei 2026-11-13 16:18 and 17:07. Write this file before the work plan. Use 3-6 milestones. Each milestone delivers one runnable, verifiable result. Do not split a milestone by tech layer. Slots M4, M5, and M6 are optional; delete the ones this repo does not use.

The new-repo order is in [README.md](../README.md).

## Gate

Chief reviews each milestone. Kuei approves it before work starts.

## One pull request per milestone

Cut `milestone/<id>` from `main`.

Each ticket's agent commits and pushes on that branch. There is no ticket pull request (`autoCreatePR` off). Parallel tickets rebase onto the latest `milestone/<id>` before pushing.

CI runs on push to `milestone/**`. [`.github/workflows/docs.yml`](../../.github/workflows/docs.yml) uses `branches-ignore: main`, so those pushes are included.

Each ticket records a report in its ticket file: the handoff fields in [AGENTS.md](../../AGENTS.md), plus that ticket's commit range. Vera verifies every ticket. A dependent ticket starts only after her PASS.

When every ticket has a PASS, bullet-bots opens one pull request from `milestone/<id>` to `main`. The body aggregates each ticket's handoff fields and links Vera's verdicts.

After that pull request is open, `@claude` review comments and red CI go back to the owning ticket's agent.

## M1

- Goal: <one line>
- Done-when: <verifiable result>
- In scope: <included>
- Out of scope: <excluded>
- Dependencies: <none or earlier milestone ids>
- Gate: <pending, or approved YYYY-MM-DD HH:MM>

## M2

- Goal: <one line>
- Done-when: <verifiable result>
- In scope: <included>
- Out of scope: <excluded>
- Dependencies: <none or earlier milestone ids>
- Gate: <pending, or approved YYYY-MM-DD HH:MM>

## M3

- Goal: <one line>
- Done-when: <verifiable result>
- In scope: <included>
- Out of scope: <excluded>
- Dependencies: <none or earlier milestone ids>
- Gate: <pending, or approved YYYY-MM-DD HH:MM>

## M4

- Goal: <one line>
- Done-when: <verifiable result>
- In scope: <included>
- Out of scope: <excluded>
- Dependencies: <none or earlier milestone ids>
- Gate: <pending, or approved YYYY-MM-DD HH:MM>

## M5

- Goal: <one line>
- Done-when: <verifiable result>
- In scope: <included>
- Out of scope: <excluded>
- Dependencies: <none or earlier milestone ids>
- Gate: <pending, or approved YYYY-MM-DD HH:MM>

## M6

- Goal: <one line>
- Done-when: <verifiable result>
- In scope: <included>
- Out of scope: <excluded>
- Dependencies: <none or earlier milestone ids>
- Gate: <pending, or approved YYYY-MM-DD HH:MM>
