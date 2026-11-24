# Endpoints, imaging & device lifecycle

[← Back to overview](../README.md)

| ID | Type | Item | Metric |
|---|---|---|---|
| [EP-01](#ep-01) | 🟦 WORK | Laptop imaging from an hour to minutes | ~60 → ~15 min per device |
| [EP-02](#ep-02) | 🟦 WORK | Imaging capacity for a region | ~10 → ~50 computers per hour |
| [EP-03](#ep-03) | 🟦 WORK | Imaging network upgrade | 100 Mbps → 1 Gbps |
| [EP-04](#ep-04) | 🟦 WORK | Mac and Windows preparation | not measured |
| [EP-05](#ep-05) | 🟦 WORK | Large workstation rollout | ~400 devices |

## EP-01
### Laptop imaging from an hour to minutes  ·  🟦 WORK

| Before | After |
|---|---|
| Imaging failed almost daily, images were out of date and each technician checked devices differently. | Breakages stopped reaching users; one standard for every technician. |

**What I built or changed:** Upgraded the imaging servers, kept OS builds current, set up a daily image test, scripted update and component checks, and standardised wipe-and-reimage with a checklist.

**Tools:** Imaging servers (Linux & Windows), scripts, checklist  ·  **Metric:** ~60 → ~15 min per device  ·  **Evidence:** Sanitised case study, readiness script, checklist

**How to do it (teaching notes):**

1. Measure the current time per device on a few machines.
2. Keep a test machine that images every morning.
3. Script the checks you do by hand (camera, audio, network, updates).
4. Turn the steps into one checklist and train everyone on it.
5. Measure again with the same method.

---

## EP-02
### Imaging capacity for a region  ·  🟦 WORK

| Before | After |
|---|---|
| Imaging capacity was too low for regional deployments. | More devices imaged per hour; images validated across regions. |

**What I built or changed:** Installed and configured Linux and Windows imaging servers for EMEA and another region, and tested new images with engineers in APAC.

**Tools:** Imaging servers  ·  **Metric:** ~10 → ~50 computers per hour  ·  **Evidence:** Portfolio table

**How to do it (teaching notes):**

1. Place an imaging server close to each large site.
2. Share one golden image and test it in each region before release.

---

## EP-03
### Imaging network upgrade  ·  🟦 WORK

| Before | After |
|---|---|
| The imaging network ran at 100 Mbps. | Faster image transfer. |

**What I built or changed:** Worked on the upgrade of the imaging network.

**Tools:** Switching, cabling  ·  **Metric:** 100 Mbps → 1 Gbps  ·  **Evidence:** Case study

**How to do it (teaching notes):**

1. Measure transfer time first.
2. Upgrade the uplink and switch ports for the imaging VLAN.
3. Measure again.

---

## EP-04
### Mac and Windows preparation  ·  🟦 WORK

| Before | After |
|---|---|
| Corporate laptops needed encryption and configuration before handover. | Every device encrypted and managed before handover. |

**What I built or changed:** Registered Macs in Apple Business Manager and configured them with Puppet; prepared Windows laptops with BitLocker and recovery keys in MBAM.

**Tools:** Apple Business Manager, Puppet, BitLocker, MBAM  ·  **Metric:** not measured  ·  **Evidence:** Tool mapping to Intune/Jamf

**How to do it (teaching notes):**

1. Enrol the device in the management platform.
2. Apply the baseline configuration.
3. Confirm encryption and escrowed recovery key.
4. Hand over only after the check passes.

---

## EP-05
### Large workstation rollout  ·  🟦 WORK

| Before | After |
|---|---|
| A new site needed workstations ready on time. | Site delivered ready for users. |

**What I built or changed:** Took part in setup and readiness checks for the rollout and fixed issues on the spot.

**Tools:** Windows endpoints, imaging  ·  **Metric:** ~400 devices  ·  **Evidence:** Case study

**How to do it (teaching notes):**

1. Image in batches.
2. Run the same readiness checklist on every desk.
3. Log faults and fix before the users arrive.

---
