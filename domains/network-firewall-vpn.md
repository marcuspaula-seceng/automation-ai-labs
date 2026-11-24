# Network, firewall & VPN support

[← Back to overview](../README.md)

| ID | Type | Item | Metric |
|---|---|---|---|
| [NW-01](#nw-01) | 🟦 WORK | Firewall and VPN requests with evidence | not measured |
| [NW-02](#nw-02) | 🟩 LAB | Firewall change discipline | 19 Pester tests |

## NW-01
### Firewall and VPN requests with evidence  ·  🟦 WORK

| Before | After |
|---|---|
| Access requests reached the network team without detail. | Escalations arrived with evidence; the network team owned the firewall. |

**What I built or changed:** Collected source, destination, port and reason; raised the request; tested after the network team applied it; troubleshot VPN, DNS and ports before escalating.

**Tools:** VPN, nslookup, Test-NetConnection  ·  **Metric:** not measured  ·  **Evidence:** none

**How to do it (teaching notes):**

1. `nslookup <name>` to check DNS.
2. `Test-NetConnection <host> -Port <port>` to check reachability.
3. Attach both outputs to the ticket before escalating.

---

## NW-02
### Firewall change discipline  ·  🟩 LAB

| Before | After |
|---|---|
| Firewall changes need backup and rollback. | Guide and tests ready; lab not executed yet. |

**What I built or changed:** Wrote a change record, a backup-change-verify-rollback guide and a read-only network path test for before/after evidence.

**Tools:** PowerShell, Pester  ·  **Metric:** 19 Pester tests  ·  **Evidence:** Guide, script, tests

**How to do it (teaching notes):**

1. Back up the configuration.
2. Run the path test before.
3. Make the change in the window.
4. Run the path test after and compare.
5. Roll back if any test fails.

---
