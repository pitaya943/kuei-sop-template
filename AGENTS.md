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
- Roles / 角色：Alex `<drafts the work plan>`，Chief `<reviews the plan>`，Vera `<verification; PASS before @claude review>`，Kuei `<approves done-when and merges>`。
- Vera PASS 之後，每個 PR 都跑 @claude review，然後 Kuei merge。Claude 額度用完時，Kuei 可不等該次 @claude review 直接合併，須記錄。When the Claude quota is exhausted, Kuei may merge without waiting for that @claude review, and it must be recorded.
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

Flow / 流程: Alex drafts → Chief reviews → Kuei approves each ticket's done-when in the ticket file → independent tickets run in parallel. 各自獨立的工單並行，不把整件事交給一個 agent 依序做完。完成條件在工單檔。
Model / 模型: Never Opus. Fix rounds use a stronger model, and if none is stronger keep the same model and record it. Verification uses a different model family. 修復輪用更強的模型；沒有更強的就沿用同一模型並記錄。驗證用不同模型家族。
Source / 準據: [docs/work-plan-template.md](docs/work-plan-template.md). 以 docs 檔為準 / the docs file wins.

## 開發規則 / Development rules

Kuei decisions 2026-11-11 19:57、20:10、20:22（via Chief）。專案路徑與指令用 `<placeholder>`。

1. **Spec first（SDD）**：規格在 `<spec path>`。規格不清楚就停，在 PR 問；不要猜。
2. **先寫會失敗的測試，再寫實作**（TDD/BDD）。
3. **每個拒絕案例**都斷言三件事：精確的 status code、精確的錯誤訊息、沒有寫入任何資料（含沒有寫到一半的資料）。
4. **伺服器重驗每一個欄位**；不信任前端。缺值不得悄悄補預設值。
5. **系統級規則先做逐項盤點表**；每一列都有 spec source、檢查位置（file:line）、test name。表的位置：`<inventory table path>`。
6. **CI 全綠才算完成。** CI 不得自動 commit。只有 bullet-bots commit；唯一例外是 @claude review：Kuei 要求時，Claude 可直接推修正 commit。When Kuei asks, Claude may push fix commits directly to the PR branch.
7. **不 push main、不 force-push、不 merge。** 不碰 secrets；程式與 log 都不印 key。只改自己這張工單範圍內的檔案。
8. **Never Opus。**
9. **PR 報告中英並列**：做了什麼、證據（指令與結果）、未解問題、需要 Kuei 決定的事。指令：`<test commands>`。

## 預算備註
- Claude Pro 額度緊：對齊、學習，以及 Vera PASS 之後每個 PR 的 @claude review
- 訂閱額度用完時會顯示重置時間（例如「5-hour limit reached - resets [time]」），不是 HTTP 429；429 屬於 API key 或容量問題
- GitHub Action（`@claude`）可能與 claude.ai／Claude Code web 共用同一份 Pro 額度（推論，官方未明說）
- <本專案的其他限制>

## Docs / 文件

Standing doc rules are only in [docs/README.md](docs/README.md). If this file and `docs/` disagree, docs wins.
文件規則只寫在 [docs/README.md](docs/README.md)。本檔與 `docs/` 不一致時，以 docs 為準。
