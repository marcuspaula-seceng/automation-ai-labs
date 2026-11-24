# Commands & events cheat-sheet

[← Back to overview](README.md)

## Troubleshooting before escalation

| Command | What it tells you |
|---|---|
| `nslookup <name>` | Does the name resolve? |
| `Test-NetConnection <host> -Port <port>` | Is the port reachable from this machine? |
| `Get-NetTCPConnection -LocalPort <port>` | Who is already listening on a port? |
| `Get-Process -Id <pid>` | Which process owns that listener? |
| `Invoke-RestMethod <url>/health` | Is the service actually ready, not just running? |

## Identity and endpoints (PowerShell)

| Command | Use |
|---|---|
| `Get-ADUser -Filter * -Properties LastLogonDate` | Find stale accounts for an access review |
| `Get-EndpointReadiness.ps1` | Read-only readiness check after imaging |
| `Get-UserAccessSnapshot.ps1 -UserPrincipalName <upn>` | Read-only view of a user's groups, licences and devices |
| JML module with `-WhatIf` | Plan joiner/mover/leaver actions before changing anything |
| `Invoke-Pester ./tests -Output Detailed` | Run the test suite; every Graph call is mocked |

## Automation and pipelines

| Command | Use |
|---|---|
| `robocopy <src> <dst> /E` | Additive backup: copies, never deletes (avoid `/MIR` for backups) |
| `docker compose up -d` | Start a lab stack |
| `docker volume inspect <name>` | Confirm a data volume exists before creating a container |
| `sqlite3 <db> "PRAGMA integrity_check;"` | Check a database before migrating it |
| `promtool check rules` / `promtool test rules` | Validate and unit-test alert rules |
| `python -m unittest discover -s tests` | Run standard-library tests |
| `powercfg /change standby-timeout-ac 0` | Keep a lab host awake 24/7 |
| `wsl --shutdown` · `wsl --update` | Recover a stuck WSL2 environment |

## Jira Service Management

| Item | Example |
|---|---|
| Queue: unassigned, close to SLA breach | `resolution = Unresolved AND assignee is EMPTY ORDER BY "Time to first response" ASC` |
| Automation | When a work item is created, if the request type is New starter, create 4 sub-tasks |
| Automation | When a repair request opens, set the linked laptop's status to In repair |
| Diagnose a failed rule | Open the automation audit log *before* changing the rule |

## Events: how a good incident reads

1. **09:00** Major incident declared. First user update with the next update time.
2. **09:05** Scope confirmed (who and what is affected).
3. **09:20** Cause isolated; supplier ticket raised with evidence.
4. **09:50** Service restored; sign-in tested.
5. **After:** problem record with root cause, workaround and permanent fix → normal change → review → CAB → window → tests → close.
