# Attack Simulation – SSH Brute Force

---

## 1. Overview

This phase simulates an SSH brute force attack to replicate a common real-world technique used by attackers to gain unauthorized access to systems.

The activity generates authentication failure logs, which are later used to validate SIEM detection and response capabilities.

---

## 2. Objective

The objective of this simulation is to:

* Generate repeated failed authentication attempts
* Validate log generation on the target system
* Enable SIEM-based detection of brute force behavior
* Prepare data for detection engineering and incident analysis

---

## 3. Target

The **Ubuntu server** was selected as the target system.

* SSH service is enabled and exposed
* The system is monitored by the Wazuh agent
* Authentication logs are actively collected

---

## 4. Attack Methodology

A dictionary-based brute force attack was conducted using a predefined password list to simulate attacker behavior.

This method attempts multiple password combinations against a valid username to gain access.

---

## 5. Tool Used

**Hydra** was used to perform the attack.

Hydra is a widely used password-cracking tool that supports multiple protocols, including SSH, FTP, and HTTP.

---

## 6. Execution

### Attack Command

```bash id="k8n2zp"
hydra -l ubuntu -P /usr/share/wordlists/rockyou.txt ssh://192.168.239.4
```

### Command Breakdown

* `-l ubuntu` → Target username
* `-P rockyou.txt` → Password wordlist
* `ssh://` → Target protocol
* Target IP → Ubuntu server

---

## 7. Observations

During execution:

* Multiple failed login attempts were generated
* The target system recorded authentication failures in `/var/log/auth.log`
* Logs included source IP, username, and timestamps

These logs are critical for identifying brute force patterns.

---

## 8. Security Impact

Brute force attacks pose significant risks:

* Unauthorized access if weak credentials exist
* Account compromise
* Potential privilege escalation

Continuous monitoring of authentication logs is essential to detect and prevent such attacks.

---

## 9. MITRE ATT&CK Mapping

This activity maps to:

```text id="m2nq4r"
T1110 – Brute Force
```

Attackers use this technique to guess passwords and gain access to systems.

---

## 10. Detection Relevance

This simulation provides the necessary log data for:

* SIEM-based detection rules
* Custom rule development in Wazuh
* Alert generation and correlation

It serves as the foundation for the **Detection Engineering phase**.

---

## 11. Evidence Collection

Screenshots were captured to validate attack execution and log generation.

> **Note:** Store all images inside the repository and use relative paths.

---

## 12. Conclusion

This phase successfully simulated an SSH brute force attack and generated authentication logs on the target system.

These logs will be used in subsequent phases to:

* Detect malicious behavior using Wazuh
* Develop custom detection rules
* Trigger automated response mechanisms

---

## 13. Supporting Evidence

![Hydra Attack Output](../images/hydra-attc.png)

![Wazuh Logs](../images/w-logs.png)

![Agent Logs](../images/agent-logs.png)

![Auth Log Evidence](../images/auth-log.png)

---
