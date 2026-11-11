# kuei-sop-template

Template repository for Kuei’s AI collaboration SOP（AI 協作 SOP 範本 repo）.

## How to use / 怎麼用

1. On GitHub, open this repo and click **Use this template** → create a new private (or public) repo.
   在 GitHub 開啟本 repo，點 **Use this template**，建立新專案 repo。
2. Fill in the placeholders in `AGENTS.md` (project type, goal, milestones, decision gates, review depth, budget notes).
   填寫 `AGENTS.md` 裡的 placeholder（類型、目標、milestones、重要決策、審查深度、預算備註）。
3. Keep or trim `.claude/skills/` (`grill-me`, `teach` by default). Add project-specific skills only when needed.
   預設保留 `.claude/skills/` 的 `grill-me`、`teach`；專案需要時再加其他 skill。
4. Record decisions in `docs/decisions.md` and milestone summaries under `docs/milestones/`.
   決策寫進 `docs/decisions.md`，每個 milestone 摘要放 `docs/milestones/`。
5. You still need to set branch protection on `main`, install/authorize the Claude GitHub App for the new repo, and add the repo secret `CLAUDE_CODE_OAUTH_TOKEN` (see below).
   新專案還要自行設定 `main` 的 branch protection、把 Claude GitHub App 授權到該 repo，並加入 repo secret `CLAUDE_CODE_OAUTH_TOKEN`（見下方）。

## Enable `@claude` review on PRs / 啟用 PR 上的 `@claude` 審查

This template includes [`.github/workflows/claude.yml`](.github/workflows/claude.yml) from the official [anthropics/claude-code-action](https://github.com/anthropics/claude-code-action) `@v1` example. Commenting `@claude review` (or any `@claude …`) on a PR or issue triggers Claude.
本範本內建官方 [anthropics/claude-code-action](https://github.com/anthropics/claude-code-action) `@v1` 範例的 [`.github/workflows/claude.yml`](.github/workflows/claude.yml)。在 PR 或 issue 留言 `@claude review`（或任何 `@claude …`）就會觸發 Claude。

In each **new** repo created from this template:
用這個範本建立的**新** repo 還要：

1. Install and authorize the [Claude GitHub App](https://github.com/apps/claude) on that repo (or keep “All repositories” if you already use Claude Desktop cloud sessions).
   為該 repo 安裝並授權 [Claude GitHub App](https://github.com/apps/claude)（若你用 Claude Desktop 的 cloud session，可維持「All repositories」）。
2. Add a repository secret named `CLAUDE_CODE_OAUTH_TOKEN`. Create the token locally with `claude setup-token` (Claude Pro / Max). Do not paste the token into chat.
   在 repo Settings → Secrets and variables → Actions 新增 `CLAUDE_CODE_OAUTH_TOKEN`。本機用 `claude setup-token` 產生（Claude Pro / Max）。不要把 token 貼到聊天。
3. On a PR, comment `@claude review` (or another `@claude …` instruction).
   在 PR 上留言 `@claude review`（或其他 `@claude …` 指示）。

Source: workflow adapted from https://github.com/anthropics/claude-code-action/blob/v1/examples/claude.yml — uses `claude_code_oauth_token` instead of `anthropic_api_key` because this SOP assumes a Claude Pro subscription.
來源：依 https://github.com/anthropics/claude-code-action/blob/v1/examples/claude.yml 調整；改用 `claude_code_oauth_token`（本 SOP 假設使用 Claude Pro 訂閱）。

## Layout / 結構

- `AGENTS.md` — per-project settings template
- `CLAUDE.md` — one-line pointer to `AGENTS.md`
- `.claude/skills/grill-me/`, `.claude/skills/teach/` — from [mattpocock/skills](https://github.com/mattpocock/skills) (MIT)
- `docs/decisions.md` — decision log table
- `docs/README.md` — docs index and the rule that docs wins / 文件索引，以及以 docs 為準
- `docs/work-plan-template.md` — work-plan source of truth / 分工計畫的唯一來源
- `docs/work-plans/` — approved work plans (`<id>.md`) / 已核可的分工計畫
- `docs/milestones/` — milestone summary folder
- `.github/workflows/claude.yml` — `@claude` mention trigger (needs App + secret)

## License note for vendored skills

The files under `.claude/skills/grill-me/` and `.claude/skills/teach/` are copied from mattpocock/skills under the MIT License. See each folder’s `LICENSE` and `SOURCE.md`.
