# Approvals, change & logistics

[← Back to overview](../README.md)

| ID | Type | Item | Metric |
|---|---|---|---|
| [AP-01](#ap-01) | 🟦 WORK | Software request and approval | not measured |
| [AP-02](#ap-02) | 🟩 LAB | Manager approval and a real failure | not measured |
| [AP-03](#ap-03) | 🟦 WORK | Equipment logistics | not measured |

## AP-01
### Software request and approval  ·  🟦 WORK

| Before | After |
|---|---|
| Corporate software needed approval and licence checks before installation. | Software installed only after approval. |

**What I built or changed:** Worked through request, approval, licensing and installation checks for corporate applications.

**Tools:** Internal request tools  ·  **Metric:** not measured  ·  **Evidence:** none

**How to do it (teaching notes):**

1. Check the requester's role and the licence pool.
2. Get the approver's decision in the ticket.
3. Install and record the licence assignment.

---

## AP-02
### Manager approval and a real failure  ·  🟩 LAB

| Before | After |
|---|---|
| Access requests had no approval gate. | Approval works; failure and fix documented. |

**What I built or changed:** Added manager approval (requester cannot approve their own). When it failed, the automation audit log showed a missing workflow transition; fixed and retested.

**Tools:** Jira workflow, automation audit log  ·  **Metric:** not measured  ·  **Evidence:** Screenshots

**How to do it (teaching notes):**

1. Add an approval step to the workflow.
2. Test with a real request.
3. If it fails, read the audit log before changing anything.
4. Document symptom, cause and fix.

---

## AP-03
### Equipment logistics  ·  🟦 WORK

| Before | After |
|---|---|
| Equipment moved between staff, couriers and vendors without one process. | Devices tracked to the right place. |

**What I built or changed:** Coordinated equipment logistics with employees, couriers, vendors and internal stakeholders.

**Tools:** Logistics process, asset records  ·  **Metric:** not measured  ·  **Evidence:** none

**How to do it (teaching notes):**

1. Create the shipment record before the device leaves.
2. Update the asset record on receipt.

---
