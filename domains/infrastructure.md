# Servers, infrastructure & automation pipelines

[← Back to overview](../README.md)

| ID | Type | Item | Metric |
|---|---|---|---|
| [IN-01](#in-01) | 🟦 WORK | Virtualisation platform deployment | not measured |
| [IN-02](#in-02) | 🟦 WORK | Freelance infrastructure support | not measured |
| [IN-03](#in-03) | 🟩 LAB | Scheduled operations with Jenkins | 20 Pester tests |
| [IN-04](#in-04) | 🟩 LAB | Lab services in Docker Compose | 8 containers |
| [IN-05](#in-05) | 🟩 LAB | Domain controller failure, published | 4 attempts · 3 h 20 min |
| [IN-06](#in-06) | 🟩 LAB | Safe-by-default admin tools | 3 defects |

## IN-01
### Virtualisation platform deployment  ·  🟦 WORK

| Before | After |
|---|---|
| A new virtualisation platform was needed. | Platform deployed and validated. |

**What I built or changed:** Supported deployment: server storage, 10 Gb network adapters, vSphere/vCenter, Linux and Windows VMs.

**Tools:** VMware vSphere, vCenter  ·  **Metric:** not measured  ·  **Evidence:** Deployment and validation checklists

**How to do it (teaching notes):**

1. Install storage and NICs, check firmware.
2. Deploy hosts and vCenter.
3. Provision a test VM per OS and validate network and storage.

---

## IN-02
### Freelance infrastructure support  ·  🟦 WORK

| Before | After |
|---|---|
| A small organisation had no in-house IT. | not measured |

**What I built or changed:** Provided infrastructure and end-user support: endpoints, Microsoft 365, networking and accounts.

**Tools:** Windows, Linux, macOS, Microsoft 365  ·  **Metric:** not measured  ·  **Evidence:** none

**How to do it (teaching notes):**

1. Inventory every device and account first.
2. Standardise accounts and backups before anything else.

---

## IN-03
### Scheduled operations with Jenkins  ·  🟩 LAB

| Before | After |
|---|---|
| Checks and backups were run by hand. | Unattended checks and backups; a missing backup target reports UNSTABLE instead of FAILED. |

**What I built or changed:** Set up a Jenkins Windows agent with an hourly site and TLS certificate check and dated and nightly additive backups. Fixed a duplicate-agent handshake loop with a single-instance guard.

**Tools:** Jenkins, PowerShell, Pester  ·  **Metric:** 20 Pester tests  ·  **Evidence:** Scripts, Jenkinsfiles, runbook

**How to do it (teaching notes):**

1. Install the agent as a service.
2. One Jenkinsfile per job: site-health, backup-snapshot, backup-nas.
3. Use robocopy `/E` (never `/MIR`) so a backup never deletes.
4. Write the runbook from the real faults you hit.

---

## IN-04
### Lab services in Docker Compose  ·  🟩 LAB

| Before | After |
|---|---|
| Lab services ran loose on the host. | Lighter host, no data lost. |

**What I built or changed:** Moved CI, identity, file-share and local-LLM services into one Compose project with pinned volumes and a 30-minute container health watcher.

**Tools:** Docker Compose, PowerShell  ·  **Metric:** 8 containers  ·  **Evidence:** Compose files

**How to do it (teaching notes):**

1. Pin image versions and volume names.
2. Bind ports to 127.0.0.1.
3. Watch expected containers on a schedule and alert if one is missing.

---

## IN-05
### Domain controller failure, published  ·  🟩 LAB

| Before | After |
|---|---|
| Domain controller promotion failed repeatedly. | Failure understood; rebuild in progress. |

**What I built or changed:** Published 4 failed promotions with raw logs, found the root cause (AD DS role never installed) and a defect in my own control script.

**Tools:** VirtualBox, Windows Server, PowerShell  ·  **Metric:** 4 attempts · 3 h 20 min  ·  **Evidence:** Raw logs

**How to do it (teaching notes):**

1. Snapshot before each risky step.
2. Check the outcome, not just that the VM is alive.
3. Publish the failure and the fix.

---

## IN-06
### Safe-by-default admin tools  ·  🟩 LAB

| Before | After |
|---|---|
| Small admin tools can cause damage on error. | 3 defects found on day one, one of which made a report state something false. |

**What I built or changed:** Built a health check, watchdog, additive copy tool and local CI runner, and documented the additive-migration policy (read-only source, verify copies, rollback).

**Tools:** PowerShell  ·  **Metric:** 3 defects  ·  **Evidence:** Test record, policy

**How to do it (teaching notes):**

1. Default to read-only.
2. Copy, verify hashes, then report.
3. Never delete in the same run.

---
