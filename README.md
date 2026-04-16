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

### Failed Login Detection

<img width="975" height="282" alt="image" src="https://github.com/user-attachments/assets/a1696c31-3fcd-4279-801a-4e5d955b6712" />

<img width="975" height="393" alt="image" src="https://github.com/user-attachments/assets/9d06a048-97c0-4b40-bd78-2885e644a77d" />



### Possible Account Compromise

<img width="975" height="130" alt="image" src="https://github.com/user-attachments/assets/5b6ed1ed-221c-443a-8ead-5baff35959d6" />

### Possiblw Brute Force Detection

<img width="975" height="233" alt="image" src="https://github.com/user-attachments/assets/e26e9e5f-1a01-46d5-8a6d-4f8742203914" />



```

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

