# Docs

Index of the SOP docs. If this file and `AGENTS.md` disagree, this file wins.

In-repo docs are English-only. Identifiers (`AGENTS.md`, paths, role names, tool names) stay untranslated.

## Rules

| Rule | Who | When | PR check |
| --- | --- | --- | --- |
| Single source. One maintained file per fact. The work-plan source is `docs/work-plan-template.md`. A ticket's done-when lives only in `docs/tickets/T-xxx.md`. `AGENTS.md` keeps only the short summary and the link. The same PR that changes a docs fact updates the `AGENTS.md` summary. Approved plans are saved as `docs/work-plans/<id>.md`. | Alex drafts; Chief reviews; Kuei approves the done-when in the ticket file. | Draft before work. Save the plan after Kuei approves the done-when in the ticket file. | The same PR updates the `AGENTS.md` summary. No second copy of the plan or of a ticket done-when. |
| Boundary. `AGENTS.md` is standing rules only. Templates and project data live under `docs/`. `README.md` is for humans. | Alex, when a standing rule changes. Kuei fills placeholders on a new repo. | Only when a standing rule changes. | `AGENTS.md` stays a summary plus links, not a second work plan. |
| Decisions. Append a row to `docs/decisions.md` (question, choice, reason, date). A change is a new row that names the row it replaces. Keep this table until it grows, then switch to MADR files. | Alex or the Cloud Agent records a Kuei decision. | Same PR as the change, or the PR immediately after the decision. | New row has question, choice, reason, and date. Old rows are not silently rewritten. |
| Same PR. A PR that changes behaviour, a public interface, or process updates the owning doc in that PR. Derived files are regenerated in that PR, not hand-edited. In addition, a spec is living: change it in the same PR as the behaviour, and check it with tests. It is not frozen. | Alex or the Cloud Agent on that ticket. | Same PR as the behaviour, public interface, or process change. | Owning doc updated. Spec and tests updated together. |
| CI. Pull requests run markdownlint and lychee on `AGENTS.md`, `CLAUDE.md`, `README.md`, and `docs/**`. The PR template is the checklist. There is no CODEOWNERS file. Command examples that claim to be runnable must be run in CI. | The docs workflow. It reads the repo and does not commit. | Every pull request. | Both checks are green. Claimed runnable examples ran in CI. Checklist items that apply are ticked. |
| Vera. Before PASS, Vera checks the owning file, the `AGENTS.md` summary, that no parallel source was added, and that inventory citations and spec citations still resolve. Vera does not write a second product doc. | Vera. | After implementation, before merge. | PASS includes this gate. Kuei merges. |
