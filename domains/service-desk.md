# Service desk, escalation & ITSM

[← Back to overview](../README.md)

| ID | Type | Item | Metric |
|---|---|---|---|
| [SD-01](#sd-01) | 🟦 WORK | Country queues with owners and pre-assignment | SLAs from 30 min (urgent) to 24 h (low) |
| [SD-02](#sd-02) | 🟦 WORK | L2/L3 escalation point | not measured |
| [SD-03](#sd-03) | 🟦 WORK | On-call escalation with context | not measured |
| [SD-04](#sd-04) | 🟩 LAB | Full IT service desk built from scratch | 4 request types · 2 SLAs |
| [SD-05](#sd-05) | 🟩 LAB | Incident, problem and change in one scenario | 3 incidents · 1 problem · 1 change |
| [SD-06](#sd-06) | 🟩 LAB | Self-service knowledge base | 3+ articles |

## SD-01
### Country queues with owners and pre-assignment  ·  🟦 WORK

| Before | After |
|---|---|
| All tickets landed in one shared queue and ownership was unclear. | Faster first response and clear ownership. |

**What I built or changed:** Worked inside the move to queues by country, each owned by a team, with tickets routed and pre-assigned to the responsible engineer and SLAs by priority.

**Tools:** Jira (agent)  ·  **Metric:** SLAs from 30 min (urgent) to 24 h (low)  ·  **Evidence:** Lab rebuild in SD-04

**How to do it (teaching notes):**

1. List where tickets land today and which have no owner.
2. Create one queue per location or team and name one owner per queue.
3. Add an automation rule that routes by location field and pre-assigns.
4. Set SLAs by priority on business hours.
5. Review created vs resolved and SLA met vs breached every week.

---

## SD-02
### L2/L3 escalation point  ·  🟦 WORK

| Before | After |
|---|---|
| First-line tickets on identity, VPN, network, endpoints and servers stayed open. | Recurring issues documented, so the next engineer fixes them faster. |

**What I built or changed:** Owned escalated incidents end to end and turned each fix into a runbook.

**Tools:** Jira, Active Directory, VPN, Windows/Linux  ·  **Metric:** not measured  ·  **Evidence:** Runbook examples (sanitised)

**How to do it (teaching notes):**

1. Reproduce the issue and write the exact symptom.
2. Separate identity, endpoint, network and application causes.
3. Fix, then write the steps as a runbook while they are fresh.
4. Link the runbook to the ticket category so it appears next time.

---

## SD-03
### On-call escalation with context  ·  🟦 WORK

| Before | After |
|---|---|
| On-call teams were paged without enough detail to act. | The receiving team could start work immediately. |

**What I built or changed:** Sent every escalation with the ticket link, impact and first findings.

**Tools:** Jira, team messaging  ·  **Metric:** not measured  ·  **Evidence:** none

**How to do it (teaching notes):**

1. Use a fixed template: ticket link, who is affected, since when, what was tested.
2. Post it in the on-call channel and confirm someone acknowledged it.
3. Add the acknowledgement time to the ticket.

---

## SD-04
### Full IT service desk built from scratch  ·  🟩 LAB

| Before | After |
|---|---|
| I had used Jira only as an agent and needed the admin side. | Working portal service desk, tested end to end with synthetic requests. |

**What I built or changed:** Built a JSM Cloud service desk: 4 request types with forms, 2 portal groups, a business-hours SLA calendar with public holidays, first-response (1 h / 4 h) and resolution (8 h / 24 h) SLAs, and a JQL queue for unassigned tickets close to breach.

**Tools:** Jira Service Management, JQL  ·  **Metric:** 4 request types · 2 SLAs  ·  **Evidence:** Screenshots, build log, configuration

**How to do it (teaching notes):**

1. Start from the IT service template and rename request types in the user's words.
2. Group them in the portal (e.g. Accounts & access, Hardware & devices).
3. Create a business-hours calendar with holidays.
4. Add SLA goals top to bottom with JQL, catch-all last.
5. Build the queue: `resolution = Unresolved AND assignee is EMPTY ORDER BY "Time to first response" ASC`.
6. Raise a test request for every request type and check the clock.

---

## SD-05
### Incident, problem and change in one scenario  ·  🟩 LAB

| Before | After |
|---|---|
| The lab had no ITIL flow beyond requests. | Full incident → problem → change chain tested. |

**What I built or changed:** Ran an office-outage scenario: 3 incidents (1 major with a timeline and user updates), 1 problem with root cause and workaround, 1 normal change with backout and test plan approved by CAB.

**Tools:** JSM ITSM  ·  **Metric:** 3 incidents · 1 problem · 1 change  ·  **Evidence:** Screenshots

**How to do it (teaching notes):**

1. Declare the major incident and post the first user update with the next update time.
2. Record each finding as an internal note with a timestamp.
3. Resolve, then open a problem and link the incidents to it.
4. Write root cause, workaround and the permanent fix as a change.
5. Pass the change through review and CAB before the window.

---

## SD-06
### Self-service knowledge base  ·  🟩 LAB

| Before | After |
|---|---|
| Users opened tickets for things they could fix themselves. | A self-service path before the queue. |

**What I built or changed:** Linked a Confluence knowledge base to the portal so articles appear before a ticket is raised.

**Tools:** Confluence, JSM  ·  **Metric:** 3+ articles  ·  **Evidence:** Screenshot

**How to do it (teaching notes):**

1. Pick the three most common simple requests.
2. Write one short article each, with screenshots.
3. Link the space to the service desk and test the portal search.

---
