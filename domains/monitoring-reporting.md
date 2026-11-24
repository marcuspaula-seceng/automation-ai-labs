# Monitoring, reporting & management

[← Back to overview](../README.md)

| ID | Type | Item | Metric |
|---|---|---|---|
| [MO-01](#mo-01) | 🟩 LAB | Synthetic checks, alerts and runbook | 3 rules · 4 rule tests · 30 s interval |
| [MO-02](#mo-02) | 🟩 LAB | Host monitor with heartbeat | 2-minute cadence |
| [MO-03](#mo-03) | 🟩 LAB | Service desk reporting | not measured |

## MO-01
### Synthetic checks, alerts and runbook  ·  🟩 LAB

| Before | After |
|---|---|
| Outages were found only when someone reported them. | Caught a real outage of a live business website 2 minutes after go-live. |

**What I built or changed:** Prometheus Blackbox checks every 30 s against lab services and public HTTPS sites; 3 alert rules (down 2 min, slow 5 min, certificate < 14 days) with unit tests; Grafana dashboard from files; ServiceDown runbook.

**Tools:** Prometheus, Blackbox Exporter, Grafana, promtool  ·  **Metric:** 3 rules · 4 rule tests · 30 s interval  ·  **Evidence:** Config, tests, runbook

**How to do it (teaching notes):**

1. Add targets in a file, not in the UI.
2. Write alert rules with a `for:` duration.
3. Unit-test rules with `promtool test rules`, including cases that must not fire.
4. Link each alert to a runbook.

---

## MO-02
### Host monitor with heartbeat  ·  🟩 LAB

| Before | After |
|---|---|
| Services, storage, scheduled tasks and backups had no common status check. | One status view; silence is detected. |

**What I built or changed:** Scheduled PowerShell monitor with a status command, push alerts and a heartbeat that alerts if the monitor itself stops.

**Tools:** PowerShell, Task Scheduler, Event Log, ntfy, Healthchecks  ·  **Metric:** 2-minute cadence  ·  **Evidence:** Script

**How to do it (teaching notes):**

1. Run checks on a schedule.
2. Send a heartbeat ping at the end of every cycle.
3. Alert when the heartbeat is missing, not only when a check fails.

---

## MO-03
### Service desk reporting  ·  🟩 LAB

| Before | After |
|---|---|
| No view of service health. | Report set defined; SLA report still to be saved. |

**What I built or changed:** Defined the reports: created vs resolved, SLA met vs breached, backlog age.

**Tools:** JSM reports  ·  **Metric:** not measured  ·  **Evidence:** Design notes

**How to do it (teaching notes):**

1. Pick 3 reports only.
2. Review weekly with the team.
3. Change one thing at a time and watch the trend.

---
