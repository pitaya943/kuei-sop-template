# AGENTS.md — 專案設定（每個 repo 一份，依專案修改）

## 專案
- 類型：code / research
- Repo：<owner/repo>
- 目標：<一句話：這個專案要做出什麼或回答什麼>

## Milestones（每一個都要 Kuei 核可才開工）
1. <M1：名稱｜完成條件>
2. <M2：名稱｜完成條件>

## 重要決策（遇到就停下來等 Kuei）
- <例：資料模型或 API 介面變更>
- <例：安全相關邏輯>
- <例：研究假設、實驗設計、評估指標>

## 審查深度
- 一般 PR：Kuei 自己看報告
- 重要 PR：加一次跨模型審查（Grok 寫的 → @claude review）
- 重大變更：開工前再跑一次 interrogate（選用）
- `@claude review` 只是審查，不會自動跑 grill-me；需要 grill-me 時走 `claude.ai/code` session

## 啟用的 skills（放在 .claude/skills/）
- grill-me、teach：只在 `claude.ai/code` 雲端 session（或 Kuei 本機 session）載入與使用；Projects thread 與 GitHub Action（`@claude`）不算
- <本專案額外需要的，預設不加>

## 固定規則
- 做題者不閱卷：builder 與 reviewer 不同模型家族
- 只開 branch 與 PR，merge 只由 Kuei 執行
- 每個 PR 附報告：做了什麼、證據（指令與結果）、未解問題、需要 Kuei 決定的事
- 決策記在 docs/decisions.md（問題｜選擇｜理由｜日期）
- 每個 milestone 結束寫一份濃縮摘要到 docs/milestones/

## 分工計畫（一頁） / Work plan (one page)

Kuei decision 2026-11-11 19:47. One page per task, fill every blank before work starts. Blank copy: [docs/work-plan-template.md](docs/work-plan-template.md).

Flow / 流程: Alex drafts → Chief reviews → Kuei approves the done-when → work starts. Independent tickets run in parallel. Never give a whole task to one agent to do in sequence.

### 1. Tickets / 工單（dependencies + parallel）

| ID | Ticket | Depends on | Parallel group | Owner role |
|----|--------|------------|----------------|------------|
| T1 | <one outcome> | — | <A, or — if blocked> | build |
| T2 | <one outcome> | <T1 / —> | <A if no shared files with T1, else after T1> | build |

Parallel / 可並行: tickets in the same group, with no dependency on each other, run at the same time. A ticket that depends on another waits.

### 2. Done-when / 完成條件（each ticket）

| ID | Done-when（observable） |
|----|-------------------------|
| T1 | <command or check, and the result that counts as done> |
| T2 | <command or check, and the result that counts as done> |

Kuei approves this table before any ticket starts.

### 3. Model per role / 角色用哪個模型

Never Opus. This covers every role: build, fix rounds, and verification.

| Role | Model | Rule |
|------|-------|------|
| build / 實作 | <model> | Writes the ticket. |
| fix rounds / 修復輪 | <stronger model than build> | Stronger than the builder. |
| verification / 驗證 | <model> | Different model family from the builder. When only one family is available, use it and record that model in the verdict. |

Verdict / 驗證結論（fill after the check）: builder `<model>`, verifier `<model>`, family `<same / different>`, note `<if only one family: say so>`.

### 4. Usage estimate / 用量估計 and stop threshold / 停止門檻

| ID | Estimate | Notes |
|----|----------|-------|
| T1 | <e.g. N agent-turns or $X> | |
| T2 | <e.g. N agent-turns or $X> | |
| **Total** | <sum> | |

Stop threshold / 停止門檻: <number>. Stop and ask Kuei when a ticket or the total reaches this. Do not keep spending past it.

### 5. Inventory / 系統級規則盤點（own ticket）

Own ticket / 獨立工單: `<Tid>` — system-wide rules, item by item (each field, each route, each role/permission is one row). The ticket is done only when every item has its own row with spec line, file:line and test name.

| Rule | Item (field / route) | Spec source (doc + line) | Where checked (file:line) | Test name |
|------|----------------------|--------------------------|---------------------------|-----------|
| server-side validation of every field | email | <docs/spec.md:12> | <api/user.ts:40> | <rejects invalid email> |
| server-side validation of every field | display name | <docs/spec.md:13> | <api/user.ts:44> | <rejects empty display name> |
| permissions | POST /api/orders | <docs/spec.md:30> | <api/orders.ts:18> | <member cannot create order> |
| permissions | DELETE /api/orders/:id | <docs/spec.md:31> | <api/orders.ts:55> | <member cannot delete order> |

### 6. Flow reminder / 流程（do not skip）

1. Alex drafts this page.
2. Chief reviews tickets, dependencies, parallel groups, models, and the stop threshold.
3. Kuei approves the done-when column.
4. Work starts. Independent tickets run in parallel. Never hand the whole task to one agent to run in sequence.

## 預算備註
- Claude Pro 額度緊：只用在對齊、學習、重要 PR 審查
- 額度緊時不要每個 PR 都自動 `@claude`，只在重要 PR 手動加
- 訂閱額度用完時會顯示重置時間（例如「5-hour limit reached - resets [time]」），不是 HTTP 429；429 屬於 API key 或容量問題
- GitHub Action（`@claude`）可能與 claude.ai／Claude Code web 共用同一份 Pro 額度（推論，官方未明說）
- <本專案的其他限制>
