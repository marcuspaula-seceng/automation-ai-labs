# AI agents & AI automation

[← Back to overview](../README.md)

| ID | Type | Item | Metric |
|---|---|---|---|
| [AI-01](#ai-01) | 🟩 LAB | Prompt injection and excessive agency | 5/5 leaked → 1/5 (hardened prompt) → 0/5 (secret removed) · tool abuse 2/2 → 0/2 |
| [AI-02](#ai-02) | 🟩 LAB | Local AI stack in containers | SQLite integrity `ok` |
| [AI-03](#ai-03) | 🟩 LAB | Port conflict on a local AI service | not measured |
| [AI-04](#ai-04) | 🟩 LAB | Launcher with readiness gate | not measured |
| [AI-05](#ai-05) | 🟩 LAB | Local document-processing repair | not measured |
| [AI-06](#ai-06) | 🟩 LAB | Scheduled AI brief | not measured |
| [AI-07](#ai-07) | 🟩 LAB | AI-assisted portfolio audit | 89 files across 22 repositories |
| [AI-08](#ai-08) | 🟩 LAB | Self-installing runbook for an AI coding agent | not measured |

## AI-01
### Prompt injection and excessive agency  ·  🟩 LAB

| Before | After |
|---|---|
| Unclear whether a system prompt protects a secret or whether an agent obeys a poisoned file. | The model is not the security boundary: secrets out of context, tools behind code guards. |

**What I built or changed:** Measured attacks against a local LLM and built two guards from the results.

**Tools:** Python, local LLM, CI  ·  **Metric:** 5/5 leaked → 1/5 (hardened prompt) → 0/5 (secret removed) · tool abuse 2/2 → 0/2  ·  **Evidence:** Public repo, raw outputs

**How to do it (teaching notes):**

1. Write the attack set first.
2. Run it before and after each guard.
3. Commit raw outputs unedited.

---

## AI-02
### Local AI stack in containers  ·  🟩 LAB

| Before | After |
|---|---|
| AI coding sessions were costly and lost context. | Tools working; token savings tracked. |

**What I built or changed:** Ran a context-optimisation proxy, a memory service and a local model, then moved them into Docker. Fixed a vector-search dependency conflict and checked SQLite integrity before cut-over.

**Tools:** Docker, Ollama, Python, SQLite  ·  **Metric:** SQLite integrity `ok`  ·  **Evidence:** Command transcripts

**How to do it (teaching notes):**

1. Copy state into a test volume.
2. Run `PRAGMA integrity_check`.
3. Start the container on a test port.
4. Cut over only after the test port works.

---

## AI-03
### Port conflict on a local AI service  ·  🟩 LAB

| Before | After |
|---|---|
| A local memory worker failed to start on its port. | Worker ready; readiness check true. |

**What I built or changed:** Found the listener and owning process, moved the worker to an alternate port and confirmed readiness.

**Tools:** PowerShell, Node.js  ·  **Metric:** not measured  ·  **Evidence:** Command transcript

**How to do it (teaching notes):**

1. `Get-NetTCPConnection -LocalPort <p>`.
2. `Get-Process -Id <OwningProcess>`.
3. Start on another port and query the readiness endpoint.

---

## AI-04
### Launcher with readiness gate  ·  🟩 LAB

| Before | After |
|---|---|
| An AI CLI depended on a local proxy that stopped when its console closed. | Startup no longer depends on an open console. |

**What I built or changed:** Moved startup into one PowerShell launcher that starts the proxy detached and waits for readiness before opening the CLI.

**Tools:** PowerShell  ·  **Metric:** not measured  ·  **Evidence:** Script

**How to do it (teaching notes):**

1. Start dependencies detached.
2. Poll the health endpoint with a timeout.
3. Only then start the client.

---

## AI-05
### Local document-processing repair  ·  🟩 LAB

| Before | After |
|---|---|
| A local OCR and text job failed on encoding and ran twice. | Tests pass on the copy; production deployment pending. |

**What I built or changed:** Repaired it in a test copy: UTF-8 handling, error handling and duplicate-run prevention.

**Tools:** PowerShell, Python, Ollama  ·  **Metric:** not measured  ·  **Evidence:** Script

**How to do it (teaching notes):**

1. Reproduce on a copy.
2. Force UTF-8 end to end.
3. Add a lock file to stop duplicate runs.

---

## AI-06
### Scheduled AI brief  ·  🟩 LAB

| Before | After |
|---|---|
| Actionable items were buried in a busy inbox. | A short brief or a clear 'nothing urgent' result. |

**What I built or changed:** Specified a scheduled AI brief with a primary-inbox filter, a lookback window and a rule for when the source is unavailable.

**Tools:** Scheduled AI task, mail connector  ·  **Metric:** not measured  ·  **Evidence:** Run records

**How to do it (teaching notes):**

1. Filter to the primary inbox only.
2. Limit the lookback window.
3. Say 'source unavailable' instead of guessing.

---

## AI-07
### AI-assisted portfolio audit  ·  🟩 LAB

| Before | After |
|---|---|
| Public examples had documentation, test and sanitisation issues. | Fixes proposed with a correction report. |

**What I built or changed:** Reviewed public repositories against private references and recorded the fixes as pull requests.

**Tools:** GitHub PRs, PowerShell, Python, pytest, Sigma  ·  **Metric:** 89 files across 22 repositories  ·  **Evidence:** Correction report

**How to do it (teaching notes):**

1. Search every repo for names, secrets and unverified claims.
2. Fix in a branch, one PR per repo.
3. Keep a report of what changed.

---

## AI-08
### Self-installing runbook for an AI coding agent  ·  🟩 LAB

| Before | After |
|---|---|
| Setting up an AI coding agent on Windows was manual. | Repeatable setup on a new machine. |

**What I built or changed:** Wrote a runbook the agent itself follows to install, verify, configure and report its setup.

**Tools:** Markdown, PowerShell  ·  **Metric:** not measured  ·  **Evidence:** Runbook

**How to do it (teaching notes):**

1. Pre-checks, install, verify, configure, report.
2. End with a checklist the agent fills in.

---
