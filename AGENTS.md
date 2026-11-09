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

## 預算備註
- Claude Pro 額度緊：只用在對齊、學習、重要 PR 審查
- 額度緊時不要每個 PR 都自動 `@claude`，只在重要 PR 手動加
- 訂閱額度用完時會顯示重置時間（例如「5-hour limit reached - resets [time]」），不是 HTTP 429；429 屬於 API key 或容量問題
- GitHub Action（`@claude`）可能與 claude.ai／Claude Code web 共用同一份 Pro 額度（推論，官方未明說）
- <本專案的其他限制>
