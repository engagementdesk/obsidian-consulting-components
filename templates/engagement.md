---
type: engagement
engagement_id: ENG-YYYY-000
client:
status: proposed
fee_model: fixed
contract_value: 0
currency: EUR
start_date: YYYY-MM-DD
end_date:
days_sold: 0
days_used: 0
acceptance_authority:
change_control: false
---
# Engagement title

> Before you set `status: active`, three fields must be filled: `acceptance_authority`, `days_sold`
> and `end_date`. An engagement without a named acceptance authority is an engagement whose
> deliverables cannot be accepted by anyone, and you will discover that at the end.

## The engagement in one paragraph

> What the client is buying, in their words, and what changes for them when it is done.

## Scope — what is in

## Scope — what is explicitly out

> Copy this straight from the exclusions section of the winning proposal. Not a summary of it. The
> literal text, because this is the paragraph you will be re-reading in eight weeks.

## Assumptions we priced on

> Every one of these is a scope change waiting to happen. When one turns out to be false, that is not
> bad luck — it is a scope change, and it should be recorded the same day.

## Governance

| | |
|---|---|
| **Acceptance authority** | |
| **Escalation route** | |
| **Steering cadence** | |
| **Change control** | |

## Deliverables

```dataview
TABLE WITHOUT ID file.link AS Deliverable, status, due_date AS Due, submitted_date AS Submitted, accepted_date AS Accepted, value AS Value
FROM [[]]
WHERE type = "deliverable"
SORT due_date ASC
```

## Meetings

```dataview
TABLE WITHOUT ID file.link AS Meeting, meeting_date AS Date, meeting_kind AS Kind
FROM [[]]
WHERE type = "meeting"
SORT meeting_date DESC
```

## Open commitments on this engagement

```dataview
TASK
FROM [[]]
WHERE !completed
SORT due ASC
```
