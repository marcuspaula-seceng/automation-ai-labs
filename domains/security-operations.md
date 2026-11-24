# Security operations (physical and SOC)

[← Back to overview](../README.md)

| ID | Type | Item | Metric |
|---|---|---|---|
| [SE-01](#se-01) | 🟦 WORK | Physical security operations | not measured |
| [SE-02](#se-02) | 🟦 WORK | Freelance security consulting | not measured |
| [SE-03](#se-03) | 🟩 LAB | Windows detection engineering | not measured |
| [SE-04](#se-04) | 🟩 LAB | Sentinel without a workspace | 45 fixtures |
| [SE-05](#se-05) | 🟩 LAB | DFIR and threat hunting | 7 hunting queries |
| [SE-06](#se-06) | 🟨 STUDY | SOC Level 1 path | 26 rooms |

## SE-01
### Physical security operations  ·  🟦 WORK

| Before | After |
|---|---|
| Large office sites needed access control and incident reporting. | Incidents reported and handed over. |

**What I built or changed:** Access control, CCTV and alarm monitoring, incident reporting and handover.

**Tools:** Access control, CCTV  ·  **Metric:** not measured  ·  **Evidence:** none

**How to do it (teaching notes):**

1. Log every incident with time, place and action.
2. Hand over open items at shift change.

---

## SE-02
### Freelance security consulting  ·  🟦 WORK

| Before | After |
|---|---|
| A client needed security risk guidance. | not measured |

**What I built or changed:** Risk advisory, GRC and GDPR support, incident-response support.

**Tools:** GRC, GDPR  ·  **Metric:** not measured  ·  **Evidence:** none

**How to do it (teaching notes):**

1. Start with a data and risk inventory.
2. Map controls to the regulation.

---

## SE-03
### Windows detection engineering  ·  🟩 LAB

| Before | After |
|---|---|
| No detection-engineering evidence. | Rules with declared true and false positives. |

**What I built or changed:** Sigma rules for Windows validated in CI against public EVTX samples; found a field-truncation defect that kept tests green while a rule never fired.

**Tools:** Sigma, Python, GitHub Actions  ·  **Metric:** not measured  ·  **Evidence:** Public repo, CI

**How to do it (teaching notes):**

1. Write the rule.
2. Declare one sample that must match and one that must not.
3. Fail CI if either case is wrong.

---

## SE-04
### Sentinel without a workspace  ·  🟩 LAB

| Before | After |
|---|---|
| Sentinel rules can't be tested without a tenant. | Rules testable locally. |

**What I built or changed:** 4 analytics rules, a local KQL evaluator, a correlation case, an automation rule and a read-only triage playbook.

**Tools:** KQL, Python  ·  **Metric:** 45 fixtures  ·  **Evidence:** Public repo, CI

**How to do it (teaching notes):**

1. Write fixtures as JSON rows.
2. Evaluate the KQL subset locally.
3. Run in CI on every push.

---

## SE-05
### DFIR and threat hunting  ·  🟩 LAB

| Before | After |
|---|---|
| No incident-response method on file. | Repeatable first response and hunting. |

**What I built or changed:** DFIR runbooks, triage scripts, chain of custody and evidence templates; AWS hunting queries with Terraform.

**Tools:** PowerShell, Bash, Athena, Terraform  ·  **Metric:** 7 hunting queries  ·  **Evidence:** Public repos

**How to do it (teaching notes):**

1. Collect volatile evidence first.
2. Hash every artefact.
3. Record who handled what and when.

---

## SE-06
### SOC Level 1 path  ·  🟨 STUDY

| Before | After |
|---|---|
| SOC skills were not yet evidenced. | Step-by-step write-ups with screenshots. |

**What I built or changed:** Completed and documented SOC Level 1 rooms: SIEM, Splunk, EDR, SOAR, malware, MITRE, kill chains, phishing, Wireshark.

**Tools:** Splunk, Wireshark, ATT&CK Navigator, ANY.RUN  ·  **Metric:** 26 rooms  ·  **Evidence:** Public repo

**How to do it (teaching notes):**

1. Read the task, answer, then write how you found it.
2. Keep one screenshot per key step.
3. Redact flags.

---
