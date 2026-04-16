# Brute-Force-Detection-Lab-Splunk-
Brute Force demonstration and detection using Splunk

🛡️ Brute Force Attack Detection Lab (Splunk SIEM)

## Overview

This project demonstrates detection of brute-force login attacks using Splunk SIEM. A lab environment was created with an endpoint system and a Splunk instance to simulate attacks, ingest logs, and build detection logic.

---

## Lab Environment

* **VM 1:** Endpoint (Windows RDP)
* **VM 2:** Splunk SIEM
* **Log Forwarding:** Splunk Universal Forwarder

---

## Attack Simulation

* Multiple failed login attempts were generated
* Followed by a successful login to simulate compromise

---

 ## Detection Use Cases
1. Brute Force Detection
  Detect multiple failed logins within a short time window.

2. Top Targeted Users
  Identify accounts under attack.

3. Top Source IPs
  Identify attacker IP addresses.

4. Possible Account Compromise
  Detect successful login after multiple failures.

---


## Splunk Queries

### Brute Force Detection

```spl
index=* ("Failed password" OR EventCode=4625)
| eval username=coalesce(user, Account_Name, TargetUserName)
| eval source_ip=coalesce(src, Source_Network_Address, rhost, client_ip)
| bin _time span=10m
| stats count by _time, username, source_ip
| where count >= 3
```

---

### Possible Account Compromise

```spl
index=* ("Failed password" OR "Accepted password" OR EventCode=4624 OR EventCode=4625)
| eval username=coalesce(user, Account_Name, TargetUserName)
| eval action=case(
    searchmatch("Failed password") OR EventCode=4625, "failed",
    searchmatch("Accepted password") OR EventCode=4624, "success"
)
| bin _time span=15m
| stats values(action) as actions by username, source_ip, _time
| where mvcount(actions) > 1
```

---

## MITRE ATT&CK Mapping

* **T1110 – Brute Force**
* Tactic: Credential Access

---

## Project Structure

* `queries/` → SPL detection queries
* `dashboards/` → Dashboard configurations
* `reports/` → Incident report
* `screenshots/` → Proof of detection
* `lab_setup/` → Setup instructions

---

## Skills Demonstrated

* SIEM (Splunk)
* Log Analysis
* Threat Detection
* SOC Workflow
* Incident Reporting

---

## Conclusion

This lab simulates a real-world brute-force attack and demonstrates detection, analysis, and reporting using Splunk.

---

