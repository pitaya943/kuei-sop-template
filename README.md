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
5. You still need to set branch protection on `main` and install/authorize the Claude GitHub App for the new repo (account steps, not part of this template).
   新專案還要自行設定 `main` 的 branch protection，並把 Claude GitHub App 授權到該 repo。

## Layout / 結構

- `AGENTS.md` — per-project settings template
- `CLAUDE.md` — one-line pointer to `AGENTS.md`
- `.claude/skills/grill-me/`, `.claude/skills/teach/` — from [mattpocock/skills](https://github.com/mattpocock/skills) (MIT)
- `docs/decisions.md` — decision log table
- `docs/milestones/` — milestone summary folder

## License note for vendored skills

The files under `.claude/skills/grill-me/` and `.claude/skills/teach/` are copied from mattpocock/skills under the MIT License. See each folder’s `LICENSE` and `SOURCE.md`.
