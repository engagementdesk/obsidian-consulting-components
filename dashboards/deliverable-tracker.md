---
type: dashboard
---
# Deliverable tracker

Four queries. Requires the Dataview plugin.

These queries scan the whole vault and filter on `type: deliverable`, so they work wherever you put
your notes. If you keep deliverables in one folder, add a source for speed — for example
`FROM "05 Deliverables"` on the line after `TABLE ...`.

## Overdue

```dataview
TABLE WITHOUT ID file.link AS Deliverable, engagement AS Engagement, status AS Status, due_date AS Due
WHERE type = "deliverable" AND due_date AND due_date < date(today) AND status != "accepted" AND status != "rejected"
SORT due_date ASC
```

## Submitted, waiting on acceptance

The gap between submission and acceptance predicts how long a client will take to pay.

```dataview
TABLE WITHOUT ID file.link AS Deliverable, engagement AS Engagement, submitted_date AS Submitted, (date(today) - date(submitted_date)).days AS "Days waiting"
WHERE type = "deliverable" AND status = "submitted"
SORT submitted_date ASC
```

## Accepted but not invoiced

Money you have earned and not asked for. This is the most common leak in an independent practice, and
it is invisible without a query.

```dataview
TABLE WITHOUT ID file.link AS Deliverable, engagement AS Engagement, accepted_date AS Accepted, value AS Value
WHERE type = "deliverable" AND status = "accepted" AND !invoice
SORT accepted_date ASC
```

## In flight

```dataview
TABLE WITHOUT ID file.link AS Deliverable, engagement AS Engagement, status AS Status, due_date AS Due, value AS Value
WHERE type = "deliverable" AND (status = "not_started" OR status = "in_progress")
SORT due_date ASC
```
