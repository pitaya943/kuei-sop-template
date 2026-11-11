# 分工計畫（一頁） / Work plan (one page)

Kuei decision 2026-11-11 19:47. Copy this page per task. Fill every blank before work starts.

Flow / 流程: Alex drafts → Chief reviews → Kuei approves the done-when → work starts. Independent tickets run in parallel. Never give a whole task to one agent to do in sequence.

## 1. Tickets / 工單（dependencies + parallel）

| ID | Ticket | Depends on | Parallel group | Owner role |
|----|--------|------------|----------------|------------|
| T1 | <one outcome> | — | <A, or — if blocked> | build |
| T2 | <one outcome> | <T1 / —> | <A if no shared files with T1, else after T1> | build |

Parallel / 可並行: tickets in the same group, with no dependency on each other, run at the same time. A ticket that depends on another waits.

## 2. Done-when / 完成條件（each ticket）

| ID | Done-when（observable） |
|----|-------------------------|
| T1 | <command or check, and the result that counts as done> |
| T2 | <command or check, and the result that counts as done> |

Kuei approves this table before any ticket starts.

## 3. Model per role / 角色用哪個模型

| Role | Model | Rule |
|------|-------|------|
| build / 實作 | <model> | Writes the ticket. |
| fix rounds / 修復輪 | <stronger model than build> | Stronger than the builder. Never Opus. |
| verification / 驗證 | <model> | Different model family from the builder. When only one family is available, use it and record that model in the verdict. |

Verdict / 驗證結論（fill after the check）: builder `<model>`, verifier `<model>`, family `<same / different>`, note `<if only one family: say so>`.

## 4. Usage estimate / 用量估計 and stop threshold / 停止門檻

| ID | Estimate | Notes |
|----|----------|-------|
| T1 | <e.g. N agent-turns or $X> | |
| T2 | <e.g. N agent-turns or $X> | |
| **Total** | <sum> | |

Stop threshold / 停止門檻: <number>. Stop and ask Kuei when a ticket or the total reaches this. Do not keep spending past it.

## 5. Inventory / 系統級規則盤點（own ticket）

Own ticket / 獨立工單: `<Tid>` — system-wide rules (e.g. server-side validation of every field, permissions). Done-when: this table is complete (every rule has spec source, check site, and test name).

| Rule | Spec source | Where it is checked (file:line) | Test name |
|------|-------------|----------------------------------|-----------|
| <e.g. server-side validation of every field> | <doc / issue / ADR> | <path:line> | <test name> |
| <e.g. permissions> | <doc / issue / ADR> | <path:line> | <test name> |

## 6. Flow reminder / 流程（do not skip）

1. Alex drafts this page.
2. Chief reviews tickets, dependencies, parallel groups, models, and the stop threshold.
3. Kuei approves the done-when column.
4. Work starts. Independent tickets run in parallel. Never hand the whole task to one agent to run in sequence.
