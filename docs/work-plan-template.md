# 分工計畫（一頁） / Work plan (one page)

Kuei decision 2026-11-11 19:47. Copy this page per task. Fill every blank before work starts. Source of truth for the work plan: this file. `AGENTS.md` must match it.

Roles / 角色：Alex `<drafts the work plan>`，Chief `<reviews the plan>`，Vera `<verification; PASS before @claude review>`，Kuei `<approves done-when and merges>`。

Flow / 流程: Alex drafts → Chief reviews → Kuei approves each ticket's done-when in the ticket file → work starts. Independent tickets run in parallel. Never give a whole task to one agent to do in sequence.

## 1. Tickets / 工單（dependencies + parallel）

| ID | depends_on | Parallel group / 可並行組 |
|----|------------|---------------------------|
| [T-000](tickets/T-000.md) | `[]` | `<A>` |
| [T-xxx](tickets/T-000.md) | `<T-000 or []>` | `<A if no shared files, else after the dependency>` |

Parallel / 可並行: tickets in the same group, with no dependency on each other, run at the same time. A ticket that depends on another waits.
可並行：同一組、且彼此沒有依賴的工單同時做。有依賴的工單要等。

## 2. Plan done-when and Kuei approval / 計畫完成條件與核可

Each ticket's done-when lives only in its ticket file. This section does not restate those criteria. It records what the whole plan must deliver, and the gate that Kuei approves every ticket done-when before work starts.
每張工單的完成條件只寫在工單檔。本節不重述那些條件。這裡只記整份計畫要交出的結果，以及開工前 Kuei 核可每張工單完成條件的關卡。

Plan-level done-when / 整份計畫的完成條件: `<what the whole plan must deliver / 整份計畫要交出什麼>`

| ID | Ticket file / 工單檔 | Kuei approved (decisions.md timestamp) / Kuei 已核可（decisions.md 時間） |
|----|----------------------|---------------------------------------------------------------------------|
| T-000 | [docs/tickets/T-000.md](tickets/T-000.md) | `<YYYY-MM-DD HH:MM>` |
| T-xxx | [docs/tickets/T-000.md](tickets/T-000.md) | `<YYYY-MM-DD HH:MM>` |

## 3. Model per role / 角色用哪個模型

Never Opus. This covers every role: build, fix rounds, and verification.

| Role | Model | Rule |
|------|-------|------|
| build / 實作 | <model> | Writes the ticket. |
| fix rounds / 修復輪 | <stronger model than build> | Stronger than the builder. If no stronger non-Opus model exists, reuse the same model and record which model was used. 找不到更強且非 Opus 的模型時，可沿用同一模型，須記錄用了哪個模型。 |
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

Own ticket / 獨立工單: `<Tid>` — system-wide rules, item by item (each field, each route, each role/permission is one row). The ticket is done only when every item has its own row with spec line, file:line and test name.

| Rule | Item (field / route) | Spec source (doc + line) | Where checked (file:line) | Test name |
|------|----------------------|--------------------------|---------------------------|-----------|
| server-side validation of every field | email | <docs/spec.md:12> | <api/user.ts:40> | <rejects invalid email> |
| server-side validation of every field | display name | <docs/spec.md:13> | <api/user.ts:44> | <rejects empty display name> |
| permissions | POST /api/orders | <docs/spec.md:30> | <api/orders.ts:18> | <member cannot create order> |
| permissions | DELETE /api/orders/:id | <docs/spec.md:31> | <api/orders.ts:55> | <member cannot delete order> |

## 6. Flow reminder / 流程（do not skip）

1. Alex drafts this page.
2. Chief reviews tickets, dependencies, parallel groups, models, and the stop threshold.
3. Kuei approves each ticket's done-when in the ticket file, and the timestamp is written in section 2. Kuei 在工單檔核可每張工單的完成條件，時間記在第 2 節。
4. Work starts. Independent tickets run in parallel. Never hand the whole task to one agent to run in sequence.
