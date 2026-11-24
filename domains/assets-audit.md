# Inventories, asset management & audit

[← Back to overview](../README.md)

| ID | Type | Item | Metric |
|---|---|---|---|
| [AS-01](#as-01) | 🟦 WORK | Scan-based asset audit | 5,000+ assets · 99% stock and audit visibility |
| [AS-02](#as-02) | 🟦 WORK | Return and redeploy workflow | 3 sites |
| [AS-03](#as-03) | 🟩 LAB | Assets (CMDB) linked to tickets | 8 synthetic laptops: 6 found, 2 wrong location, 1 missing |
| [AS-04](#as-04) | 🟩 LAB | ITAM/ITSM questions in SQL | 15 tests |

## AS-01
### Scan-based asset audit  ·  🟦 WORK

| Before | After |
|---|---|
| Stock visibility was poor. | Audit-ready inventory. |

**What I built or changed:** Defined the requirements and spreadsheet model for a scan-based asset audit; a colleague built the internal application; I supported the rollout.

**Tools:** Barcode scanning, spreadsheet model, ITAM  ·  **Metric:** 5,000+ assets · 99% stock and audit visibility  ·  **Evidence:** Reconciliation tool with tests (synthetic)

**How to do it (teaching notes):**

1. Export the expected inventory.
2. Scan every tag on the floor.
3. Reconcile: found, wrong location, missing.
4. Open a ticket for every missing item.

---

## AS-02
### Return and redeploy workflow  ·  🟦 WORK

| Before | After |
|---|---|
| Returned devices were handled differently at each site. | Same steps at every site. |

**What I built or changed:** Mapped the return workflow step by step (receipt, wipe, reimage, QC, storage, redeploy) and rolled it out.

**Tools:** Checklists, RACI  ·  **Metric:** 3 sites  ·  **Evidence:** Workflow, checklist, RACI template

**How to do it (teaching notes):**

1. Draw the flow on one page.
2. Name who owns each step (RACI).
3. Turn it into a checklist used at every site.

---

## AS-03
### Assets (CMDB) linked to tickets  ·  🟩 LAB

| Before | After |
|---|---|
| Laptops were not linked to requests. | Audit result per laptop. |

**What I built or changed:** Built a laptop schema in JSM Assets, linked laptops to requests, added an automation that updates laptop status, and ran a scan-based audit and a leaver laptop return.

**Tools:** JSM Assets, REST API  ·  **Metric:** 8 synthetic laptops: 6 found, 2 wrong location, 1 missing  ·  **Evidence:** Screenshots, procedures

**How to do it (teaching notes):**

1. Create object type Laptop with tag, owner, location, status.
2. Add an Assets field to the request types.
3. Automation: when a repair request opens, set status In repair.
4. Record audit result and last audit date per laptop.

---

## AS-04
### ITAM/ITSM questions in SQL  ·  🟩 LAB

| Before | After |
|---|---|
| Inventory and service questions were answered by hand. | Questions answered by query. |

**What I built or changed:** Built a reproducible SQLite lab: 6 tables and 5 queries (reconciliation, overdue returns, recurring incidents, resolution time).

**Tools:** SQLite, Python  ·  **Metric:** 15 tests  ·  **Evidence:** Lab guide, tests

**How to do it (teaching notes):**

1. Model assets, people, tickets and returns as tables.
2. Write one query per business question.
3. Test each query against known synthetic data.

---
