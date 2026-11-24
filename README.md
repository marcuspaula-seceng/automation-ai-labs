# Automation & AI Labs: hands-on mentor notes

**Real IT operations problems, the fix, and how to do it yourself.**

This repository collects what I have learned across years of IT operations, security and automation work, from frontline support to AI agents. Each item is written as a mentor would explain it: what was wrong **before**, what changed, the result **after**, and **step-by-step teaching notes** so you can repeat it in your own environment or home lab.

No employer, client, person or site is named. Labs use synthetic data only.

---

## How to read this repository

| Label | Meaning |
|---|---|
| 🟦 **WORK** | Done in paid work. Described at a capability level, with no internal data. |
| 🟩 **LAB** | Built and tested by me in a home or synthetic lab. |
| 🟨 **STUDY** | Learning in progress, without a finished artefact yet. |
| 🟪 **MENTORING** | Teaching, training or documentation written for others. |

Metrics appear only where they were measured. Everything else says **not measured**, because an honest "not measured" teaches more than an invented number.

---

## The journey in one line

**Frontline support → infrastructure → operations ownership → identity & endpoint security → security operations → automation & AI agents**

Each stage built on the one before, and the labs below rebuild the same skills in the open.

---

## Domains

| Domain | Work | Lab | Study / Mentoring | Highlights |
|---|---|---|---|---|
| [Service desk, escalation & ITSM](domains/service-desk.md) | 3 | 3 | 0 | SLAs from 30 min (urgent) to 24 h (low) · 4 request types · 2 SLAs · 3 incidents · 1 problem · 1 change · 3+ articles |
| [Identity, access & joiner/mover/leaver](domains/identity-jml.md) | 3 | 3 | 0 | Weekly new starters (not counted) · 31 Pester tests passing · 6/6 assertions passed |
| [Endpoints, imaging & device lifecycle](domains/endpoints-imaging.md) | 5 | 0 | 0 | ~60 → ~15 min per device · ~10 → ~50 computers per hour · 100 Mbps → 1 Gbps · ~400 devices |
| [Inventories, asset management & audit](domains/assets-audit.md) | 2 | 2 | 0 | 5,000+ assets · 99% stock and audit visibility · 3 sites · 8 synthetic laptops: 6 found, 2 wrong location, 1 missing · 15 tests |
| [Network, firewall & VPN support](domains/network-firewall-vpn.md) | 1 | 1 | 0 | 19 Pester tests |
| [Servers, infrastructure & automation pipelines](domains/infrastructure.md) | 2 | 4 | 0 | 20 Pester tests · 8 containers · 4 attempts · 3 h 20 min · 3 defects |
| [Monitoring, reporting & management](domains/monitoring-reporting.md) | 0 | 3 | 0 | 3 rules · 4 rule tests · 30 s interval · 2-minute cadence |
| [Approvals, change & logistics](domains/approvals-change.md) | 2 | 1 | 0 | - |
| [Security operations (physical and SOC)](domains/security-operations.md) | 2 | 3 | 1 | 45 fixtures · 7 hunting queries · 26 rooms |
| [AI agents & AI automation](domains/ai-agents.md) | 0 | 8 | 0 | 5/5 leaked → 1/5 (hardened prompt) → 0/5 (secret removed) · tool abuse 2/2 → 0/2 · SQLite integrity `ok` · 89 files across 22 repositories |
| [Mentoring, teaching & self-learning](domains/teaching-learning.md) | 0 | 0 | 4 | 3 manuals · 26 SOC rooms + 19 portfolio projects · ITIL 69% → 77% (pass 70%) · ~50 h Jira courses |

---

## Before → after highlights

| Area | Before | After |
|---|---|---|
| Laptop imaging | ~60 min per device, daily failures | ~15 min per device, daily image test, one checklist |
| Regional imaging | ~10 computers per hour | ~50 computers per hour |
| Imaging network | 100 Mbps | 1 Gbps |
| Asset audit | Poor stock visibility | 5,000+ assets scanned, 99% audit visibility |
| Service desk | One shared queue, unclear owners | Country queues, owners, pre-assignment, SLAs 30 min–24 h |
| JML automation (lab) | Manual account steps | `-WhatIf` plan + exceptions CSV, 31 tests passing |
| Monitoring (lab) | Outages reported by users | Alert in 2 minutes; caught a real website outage |
| AI security (lab) | Secret leaked in 5/5 attacks | 0/5 with the secret kept out of the model's context |

---

## Mentor principles behind every lab

1. **Measure before you fix.** Otherwise you can't prove the fix worked.
2. **Read-only first, `-WhatIf` first.** A tool that can't break anything by default is a tool people will trust.
3. **Test the failure, not only the success.** Every alert rule here has a test that must *not* fire.
4. **Publish the failure.** A failed domain controller promotion taught more than a clean log ever could.
5. **Separate work from lab.** Never claim a lab as production experience.
6. **The model is not the security boundary.** Keep secrets out of AI context and put tools behind code guards.

---

## Quick commands used throughout

See [commands.md](commands.md) for the command and event cheat-sheet: PowerShell, Pester, Jira automation, Prometheus, Docker and incident/change flows.

---

## Related public labs

- [cybersecurity-labs](https://github.com/marcuspaula-seceng/cybersecurity-labs): 26 SOC Level 1 rooms, step by step
- [active-directory-automation](https://github.com/marcuspaula-seceng/active-directory-automation)
- [sentinel-detection-lab](https://github.com/marcuspaula-seceng/sentinel-detection-lab)
- [windows-detection-engineering-lab](https://github.com/marcuspaula-seceng/windows-detection-engineering-lab)
- [dfir-playbook](https://github.com/marcuspaula-seceng/dfir-playbook)
- [llm-agent-security-lab](https://github.com/marcuspaula-seceng/llm-agent-security-lab)

---

*Questions or ideas? Open an issue: learning is better shared.*

Licensed under the MIT Licence.
