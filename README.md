# kuei-sop-template

Template repository for Kuei’s AI collaboration SOP.

## How to use

1. On GitHub, open this repo and click **Use this template** → create a new private (or public) repo.
2. Cut the milestones (Kuei approves) in [`docs/milestones/README.md`](docs/milestones/README.md).
3. Write the work plan for the current milestone only ([`docs/work-plan-template.md`](docs/work-plan-template.md)).
4. Fill in the remaining placeholders in `AGENTS.md` (project type, goal, decision gates).
5. Keep or trim `.claude/skills/` (`grill-me`, `teach` by default). Add project-specific skills only when needed.
6. Record decisions in `docs/decisions.md`.
7. You still need to set branch protection on `main`, install/authorize the Claude GitHub App for the new repo, and add the repo secret `CLAUDE_CODE_OAUTH_TOKEN` (see below).

## Enable `@claude` review on PRs

This template includes [`.github/workflows/claude.yml`](.github/workflows/claude.yml) from the official [anthropics/claude-code-action](https://github.com/anthropics/claude-code-action) `@v1` example. Commenting `@claude review` (or any `@claude …`) on a PR or issue triggers Claude.

In each **new** repo created from this template:

1. Install and authorize the [Claude GitHub App](https://github.com/apps/claude) on that repo (or keep “All repositories” if you already use Claude Desktop cloud sessions).
2. Add a repository secret named `CLAUDE_CODE_OAUTH_TOKEN`. Create the token locally with `claude setup-token` (Claude Pro / Max). Do not paste the token into chat.
3. On a PR, comment `@claude review` (or another `@claude …` instruction).

Source: workflow adapted from https://github.com/anthropics/claude-code-action/blob/v1/examples/claude.yml — uses `claude_code_oauth_token` instead of `anthropic_api_key` because this SOP assumes a Claude Pro subscription.

## Layout

- `AGENTS.md` — per-project settings template
- `CLAUDE.md` — one-line pointer to `AGENTS.md`
- `.claude/skills/grill-me/`, `.claude/skills/teach/` — from [mattpocock/skills](https://github.com/mattpocock/skills) (MIT)
- `docs/decisions.md` — decision log table
- `docs/README.md` — docs index and the rule that docs wins
- `docs/work-plan-template.md` — work-plan source of truth
- `docs/work-plans/` — approved work plans (`<id>.md`)
- `docs/tickets/` — ticket files (`T-xxx.md`); done-when lives only there
- `docs/milestones/README.md` — milestone template
- `docs/claude-review.md` — Claude review
- `.github/workflows/docs.yml` — markdownlint and lychee; does not commit
- `.github/workflows/claude.yml` — `@claude` mention trigger (needs App + secret)
- `.github/pull_request_template.md` — PR checklist
- `.markdownlint-cli2.yaml` — markdownlint config
- `lychee.toml` — link-check config

## License note for vendored skills

The files under `.claude/skills/grill-me/` and `.claude/skills/teach/` are copied from mattpocock/skills under the MIT License. See each folder’s `LICENSE` and `SOURCE.md`.
