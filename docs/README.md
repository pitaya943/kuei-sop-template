# Docs / 文件

Index of the SOP docs. If this file and `AGENTS.md` disagree, this file wins.
文件索引。本檔與 `AGENTS.md` 不一致時，以本檔為準。

In-repo docs are bilingual EN + 繁體中文 side by side. Identifiers (`AGENTS.md`, paths, role names, tool names) stay untranslated.
庫內文件中英並列。識別名稱（`AGENTS.md`、路徑、角色名、工具名）不翻譯。

## Rules / 規則

| Rule / 規則 | Who / 誰 | When / 何時 | PR check / 檢查 |
| --- | --- | --- | --- |
| Single source / 單一來源. One maintained file per fact. The work-plan source is `docs/work-plan-template.md`. `AGENTS.md` keeps only the short summary and the link. Approved plans are saved as `docs/work-plans/<id>.md`. 每個事實一個維護檔。`AGENTS.md` 只留短摘要與連結。核准後的計畫存 `docs/work-plans/<id>.md`。 | Alex drafts; Chief reviews; Kuei approves the done-when. Alex 起草，Chief 審，Kuei 核可 done-when。 | Draft before work. Save the file after Kuei approves the done-when. 開工前起草。Kuei 核可 done-when 後存檔。 | The summary still matches this tree. No second copy of the plan. 摘要仍與這棵樹一致。計畫沒有第二份。 |
| Boundary / 分界. `AGENTS.md` is standing rules only. Templates and project data live under `docs/`. `README.md` is for humans. `AGENTS.md` 只放常規。範本與資料在 `docs/`。`README.md` 給人看。 | Alex, when a standing rule changes. Kuei fills placeholders on a new repo. 常規變更時由 Alex 改。新 repo 的 placeholder 由 Kuei 填。 | Only when a standing rule changes. 只有常規變更時。 | `AGENTS.md` stays a summary plus links, not a second work plan. `AGENTS.md` 維持摘要加連結，不是第二份計畫。 |
| Decisions / 決策. Append a row to `docs/decisions.md` (問題｜選擇｜理由｜日期). A change is a new row that names the row it replaces. Keep this table until it grows, then switch to MADR files. 只追加列。要改就新增一列並指出被取代的列。表格先留著，變長再改 MADR 檔。 | Alex or the Cloud Agent records a Kuei decision. Alex 或 Cloud Agent 記下 Kuei 的決定。 | Same PR as the change, or the PR immediately after the decision. 與變更同一個 PR，或決定之後緊接的 PR。 | New row has 問題｜選擇｜理由｜日期. Old rows are not silently rewritten. 新列四欄齊全。舊列不默改。 |
| Same PR / 同一 PR. A spec is living: change it in the same PR as the behaviour, and check it with tests. It is not frozen. Derived files are regenerated in that PR, not hand-edited. 規格是活的：與行為同一 PR 修改，並用測試檢查。不凍結。衍生檔在該 PR 重新產生，不手改。 | Alex or the Cloud Agent on that ticket. 該工單的 Alex 或 Cloud Agent。 | Same PR as the behaviour or public interface. 與行為或公開介面同一個 PR。 | Spec and tests updated together. Citations still resolve. 規格與測試一起更新。引用仍對得上。 |
| CI / 檢查. Pull requests run markdownlint and lychee on `AGENTS.md`, `CLAUDE.md`, `README.md`, and `docs/**`. The PR template is the checklist. There is no CODEOWNERS file. PR 對這些 SOP 文件跑 markdownlint 與 lychee。PR 範本就是 checklist。沒有 CODEOWNERS。 | The docs workflow. It reads the repo and does not commit. docs workflow 只讀 repo，不 commit。 | Every pull request. 每個 PR。 | Both checks are green. Checklist items that apply are ticked. 兩項檢查都綠。適用的 checklist 已勾。 |
| Vera / 驗證. Before PASS, Vera checks the owning file, the `AGENTS.md` summary, that no parallel source was added, and that spec citations still resolve. Vera does not write a second product doc. PASS 前 Vera 核對所屬檔、摘要、沒有平行來源、引用仍對得上。Vera 不另寫一份產品文件。 | Vera. | After implementation, before merge. 實作之後、合併之前。 | PASS includes this gate. Kuei merges. PASS 含這道關卡。由 Kuei 合併。 |
