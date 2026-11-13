# Work plan (one page)

Kuei decision 2026-11-11 19:47. Copy this page and fill every blank before work starts. Source of truth for the work plan: this file. `AGENTS.md` must match it.

Current milestone: `<id>` ([section](milestones/README.md#m1)). Replace `<id>` and the `#m1` anchor with this milestone's heading. This plan covers only that milestone. The next milestone opens only after Vera PASS.

Roles: Alex `<drafts the work plan>`, Chief `<reviews the plan>`, Vera `<verification; PASS before @claude review>`, Kuei `<approves done-when and merges>`.

Flow: Alex drafts → Chief reviews → Kuei approves each ticket's done-when in the ticket file → work starts. Independent tickets run in parallel. Never give a whole task to one agent to do in sequence.

Ticket links: the `T-000` row points at the sample ticket. A `T-xxx` cell names `tickets/T-xxx.md` (section 1) or `docs/tickets/T-xxx.md` (section 2). After copying, replace that cell with a link to the new file.

## 1. Tickets (dependencies + parallel)

| ID | depends_on | Parallel group |
|----|------------|----------------|
| [T-000](tickets/T-000.md) | `[]` | `<A>` |
| `T-xxx` | `<T-000 or []>` | `<A if no shared files, else after the dependency>` |

Parallel: tickets in the same group, with no dependency on each other, run at the same time. A ticket that depends on another waits.

## 2. Plan done-when and Kuei approval

Each ticket's done-when lives only in its ticket file. This section does not restate those criteria. It records what the whole plan must deliver, and the gate that Kuei approves every ticket done-when before work starts.

The milestone in `Current milestone` is already Kuei-approved in [docs/milestones/README.md](milestones/README.md) before this plan is written.

Plan-level done-when: `<what the whole plan must deliver>`

| ID | Ticket file | Kuei approved (decisions.md timestamp) |
|----|-------------|----------------------------------------|
| T-000 | [docs/tickets/T-000.md](tickets/T-000.md) | `<YYYY-MM-DD HH:MM>` |
| T-xxx | `docs/tickets/T-xxx.md` | `<YYYY-MM-DD HH:MM>` |

## 3. Model per role

Follow the standing model rule in [AGENTS.md](../AGENTS.md). The table covers every role: build, fix rounds, and verification.

| Role | Model | Rule |
|------|-------|------|
| build | <model> | Writes the ticket. |
| fix rounds | <stronger model than build> | Stronger than the builder. If no stronger model allowed by the standing model rule exists, reuse the same model and record which model was used. |
| verification | <model> | Different model family from the builder. When only one family is available, use it and record that model in the verdict. |

Verdict (fill after the check): builder `<model>`, verifier `<model>`, family `<same / different>`, note `<if only one family: say so>`.

## 4. Inventory (own ticket)

Own ticket: `<Tid>` — system-wide rules, item by item (each field, each route, each role/permission is one row). The ticket is done only when every item has its own row with spec line, file:line and test name.

| Rule | Item (field / route) | Spec source (doc + line) | Where checked (file:line) | Test name |
|------|----------------------|--------------------------|---------------------------|-----------|
| server-side validation of every field | email | <docs/spec.md:12> | <api/user.ts:40> | <rejects invalid email> |
| server-side validation of every field | display name | <docs/spec.md:13> | <api/user.ts:44> | <rejects empty display name> |
| permissions | POST /api/orders | <docs/spec.md:30> | <api/orders.ts:18> | <member cannot create order> |
| permissions | DELETE /api/orders/:id | <docs/spec.md:31> | <api/orders.ts:55> | <member cannot delete order> |

## 5. Flow reminder (do not skip)

1. Alex drafts this page (see Current milestone and section 2).
2. Chief reviews tickets, dependencies, parallel groups, and models.
3. Major changes: run interrogate once more before work starts (optional).
4. Kuei approves each ticket's done-when in the ticket file, and the timestamp is written in section 2.
5. Work starts. Independent tickets run in parallel. Never hand the whole task to one agent to run in sequence. Delivery: [docs/milestones/README.md](milestones/README.md).
