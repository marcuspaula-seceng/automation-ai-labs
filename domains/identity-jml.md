# Identity, access & joiner/mover/leaver

[← Back to overview](../README.md)

| ID | Type | Item | Metric |
|---|---|---|---|
| [ID-01](#id-01) | 🟦 WORK | Joiner and leaver lifecycle | Weekly new starters (not counted) |
| [ID-02](#id-02) | 🟦 WORK | Safe data handover for leavers | not measured |
| [ID-03](#id-03) | 🟦 WORK | Sign-in, MFA and permission support | not measured |
| [ID-04](#id-04) | 🟩 LAB | Joiner/mover/leaver automation with Microsoft Graph | 31 Pester tests passing |
| [ID-05](#id-05) | 🟩 LAB | Active Directory access reviews | not measured |
| [ID-06](#id-06) | 🟩 LAB | File-share permissions and identity provider | 6/6 assertions passed |

## ID-01
### Joiner and leaver lifecycle  ·  🟦 WORK

| Before | After |
|---|---|
| Joiner and leaver requests arrived from the HR system and needed accounts, access and devices prepared by hand. | New starters ready on day one; leaver access removed on time. |

**What I built or changed:** Created and disabled accounts, reset passwords and MFA, assigned licences, groups and shared mailboxes; locked, wiped and recovered leaver devices.

**Tools:** Entra ID, Microsoft 365, Active Directory, HR system  ·  **Metric:** Weekly new starters (not counted)  ·  **Evidence:** Runbook, troubleshooting guide, read-only access script

**How to do it (teaching notes):**

1. Joiner: create the account, add groups by role, assign licence, enforce MFA.
2. Mover: compare old and new role groups, remove first, then add.
3. Leaver: block sign-in first, then remove groups and licences, then recover the device.
4. Record every step in the ticket.

---

## ID-02
### Safe data handover for leavers  ·  🟦 WORK

| Before | After |
|---|---|
| Leaver data transfers carried a privacy risk. | Only authorised transfers. |

**What I built or changed:** Coordinated data-ownership transfer during offboarding, with written authorisation checked before any action.

**Tools:** Offboarding process  ·  **Metric:** not measured  ·  **Evidence:** none

**How to do it (teaching notes):**

1. Ask for the approver in writing in the ticket.
2. Transfer only what was approved, to the named person.
3. Close the ticket with what was moved and when.

---

## ID-03
### Sign-in, MFA and permission support  ·  🟦 WORK

| Before | After |
|---|---|
| Users were locked out or had the wrong permissions. | Access restored without social-engineering risk. |

**What I built or changed:** Troubleshot sign-in and MFA issues and fixed group membership and permissions, always verifying identity before a reset.

**Tools:** Active Directory, Entra ID, MFA  ·  **Metric:** not measured  ·  **Evidence:** none

**How to do it (teaching notes):**

1. Verify the caller's identity through a second channel.
2. Check sign-in logs for the real error before resetting anything.
3. Fix groups, not individual permissions.

---

## ID-04
### Joiner/mover/leaver automation with Microsoft Graph  ·  🟩 LAB

| Before | After |
|---|---|
| JML steps were manual and error-prone. | Repeatable, reviewable JML runs. |

**What I built or changed:** Wrote a PowerShell module that plans JML actions from an HR feed, runs `-WhatIf` first and writes each failure to an exceptions CSV, one row per ticket.

**Tools:** PowerShell, Microsoft Graph SDK, Pester, GitHub Actions  ·  **Metric:** 31 Pester tests passing  ·  **Evidence:** Code, tests, CI run

**How to do it (teaching notes):**

1. Export the HR feed to CSV (synthetic data in the lab).
2. Build a plan object per user: create, update or disable.
3. Run with `-WhatIf` and review the plan.
4. Execute and send failures to an exceptions CSV.
5. Mock every Graph call in Pester so tests run without a tenant.

---

## ID-05
### Active Directory access reviews  ·  🟩 LAB

| Before | After |
|---|---|
| No regular review of stale or privileged accounts. | Audit reports on demand, `-WhatIf` first. |

**What I built or changed:** Scripts for onboard, transfer, offboard, access review with stale-account flagging, privileged-account audit and group-membership delta.

**Tools:** PowerShell, Pester 5, GitHub Actions  ·  **Metric:** not measured  ·  **Evidence:** Public repo + flowchart

**How to do it (teaching notes):**

1. Pull users with `Get-ADUser -Properties LastLogonDate`.
2. Flag accounts older than your inactivity threshold.
3. List members of privileged groups and compare with last month.
4. Send the report to the owner for confirm/revoke.

---

## ID-06
### File-share permissions and identity provider  ·  🟩 LAB

| Before | After |
|---|---|
| I needed to prove who can read and write what. | Access rules proven by tests. |

**What I built or changed:** Containerised Samba with 3 shares, 2 accounts and a deliberate access denial, plus Keycloak for realms and OIDC. Loopback ports, pinned images, no secrets in compose files.

**Tools:** Docker, Samba, Keycloak  ·  **Metric:** 6/6 assertions passed  ·  **Evidence:** Compose files, test output

**How to do it (teaching notes):**

1. Define shares and accounts in compose.
2. Write one test that must succeed and one that must be denied.
3. Run the tests and keep the raw output.

---
