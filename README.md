# Engagement Desk — Components

Three Obsidian components for running billable client engagements. MIT licensed.

## What this is

- **Meeting notes that emit commitments** — every commitment carries an owner and a date, so your
  backlog and the things you are blocked by stay separate.
- **An engagement record** — the engagement as the atomic unit, carrying its own commercial terms,
  scope boundary, assumptions and governance.
- **A deliverable tracker keyed on acceptance**, not on "done".

These are components, not a system. They are the parts that are useful on their own.

## Requirements

- [Obsidian](https://obsidian.md) — free to download, no account required. Licensed by its
  publisher on its publisher's own terms: <https://obsidian.md/terms>
- [Dataview](https://github.com/blacksmithgu/obsidian-dataview) — community plugin, MIT, for the
  tracker queries.

**No plugin code is bundled here.** You install Dataview yourself from Obsidian's community plugin
browser, from its own author, under its own licence. Without Dataview the tracker renders as an inert
code block and every note is still plain readable markdown.

## Install

1. Copy `templates/` and `dashboards/` into your vault.
2. Enable Dataview.
3. Point the core Templates plugin at your templates folder.
4. Open `dashboards/deliverable-tracker.md`.

## The three opinions

**Commitments have an owner and a date.** A meeting note that emits no commitments is a diary entry.
The most expensive thing in a consulting practice is something someone agreed to do that nobody wrote
down with an owner and a date — it costs you once when it is not done, and again when the client
remembers it differently. The `[owner:: client]` split matters most: those are escalations, not tasks,
and treating them as tasks is how you end up doing your client's homework unbilled.

**Scope creep is an object, not a feeling.** It is never one decision; it is eleven small ones, each
too small to be worth a difficult conversation. By the time it *feels* like scope creep you have
already absorbed it and have no record of what you absorbed. The engagement template makes assumptions
and exclusions explicit, because those are what a scope conversation points at.

**Acceptance is a state; "done" is not.** A deliverable you have finished and the client has not
accepted is not revenue — it is risk sitting on your side of the table. So `submitted` and `accepted`
are separate states with separate dates, and acceptance criteria are written before the work starts.

## Field reference

| Property | Type | Used on | Values |
|---|---|---|---|
| `type` | string | all | `meeting` · `engagement` · `deliverable` |
| `meeting_date` | date | meeting | `YYYY-MM-DD` |
| `meeting_kind` | string | meeting | `discovery` · `kickoff` · `working` · `steering` · `review` · `internal` |
| `client` | link | meeting, engagement | |
| `engagement` | link | meeting, deliverable | |
| `attendees` | list | meeting | |
| `engagement_id` | string | engagement | `ENG-2026-001` |
| `status` | string | engagement | `proposed` · `active` · `paused` · `delivered` · `closed` |
| `status` | string | deliverable | `not_started` · `in_progress` · `submitted` · `accepted` · `rejected` |
| `fee_model` | string | engagement | `fixed` · `tm` · `retainer` |
| `contract_value` | number | engagement | plain number, no symbol |
| `currency` | string | engagement | `EUR` · `GBP` · `USD` |
| `start_date` / `end_date` | date | engagement | |
| `days_sold` / `days_used` | number | engagement | |
| `acceptance_authority` | string | engagement | who signs off deliverables |
| `change_control` | boolean | engagement | is change control written into the contract? |
| `deliverable_id` | string | deliverable | `DLV-2026-001` |
| `due_date` / `submitted_date` / `accepted_date` | date | deliverable | |
| `value` | number | deliverable | |
| `invoice` | link | deliverable | empty + `accepted` = delivered and unbilled |
| `[owner:: ]` | inline | commitments | `me` · `client` |
| `[due:: ]` | inline | commitments | `YYYY-MM-DD` |

Dates are always `YYYY-MM-DD`. Money is always a plain number with the currency in its own field — a
number with a symbol in it is a string, and strings do not sum.

## The full system

These three components are part of a larger vault that adds a proposal clause library, scope-change
tracking, a pipeline, work-in-progress and receivables views, a weekly close procedure and a worked
example engagement. It is a paid download.

The full vault: <https://engagementdesk.gumroad.com/l/ablzvw>

The components in this repository are complete and usable on their own, under MIT, with no
restrictions and no upsell required.

## Licence

MIT — see [LICENSE](LICENSE).
