# Log Collection – System and Network Activity Monitoring

---

## 1. Overview

This phase focuses on monitoring system and network-related logs generated during reconnaissance and post-exploitation activities.

Unlike authentication logs, these logs capture **process execution, network connections, and system-level events**, providing deeper visibility into attacker behavior.

---

## 2. Objective

The objective of this phase is to:

* Monitor system logs during Nmap scanning and reverse shell activity
* Identify network and process-level indicators of compromise
* Validate that non-authentication attacks generate observable logs
* Ensure log availability for SIEM analysis and detection

---

## 3. Log Sources

The following log sources were monitored on the Ubuntu target system:

### System Logs

```bash
/var/log/syslog
```

### Journald Logs

```bash
journald (systemd logs)
```

### Firewall Logs (UFW)

```bash
/var/log/syslog (UFW entries)
```

---

## 4. Monitoring Method

Real-time monitoring was performed to observe system activity during attack execution.

### Commands Used

```bash id="y7o2pl"
sudo tail -f /var/log/syslog
```

```bash id="x4k9qn"
sudo journalctl -f
```

To specifically track firewall activity:

```bash id="v3d8mz"
sudo tail -f /var/log/syslog | grep UFW
```

---

## 5. Observations – Nmap Scan

During Nmap reconnaissance:

* Multiple inbound connection attempts were observed
* Sequential probing of different ports occurred
* Logs showed repeated connection activity from attacker IP

Indicators identified:

* High-frequency connection attempts
* Pattern-based port scanning behavior
* Same source IP targeting multiple ports

---

## 6. Observations – Reverse Shell Activity

During reverse shell simulation:

* Outbound connection attempts from the target system were observed
* Process execution logs indicated shell command activity
* Unexpected detection classification occurred (mapped as port scan)

This highlights how certain behaviors may overlap across detection categories.

---

## 7. Observations – Firewall (UFW)

When active response was triggered:

* Firewall rules were applied dynamically
* Blocked IP addresses were recorded
* UFW logs confirmed denied connections

Example indicators:

```text id="k1s8pz"
UFW BLOCK IN from 192.168.239.6
```

This confirms that defensive controls were successfully enforced.

---

## 8. Log Analysis

Key patterns observed across system logs:

* Repeated inbound scanning activity (Nmap)
* Outbound connection attempts (reverse shell behavior)
* Firewall enforcement actions (blocked IPs)

These logs provide strong indicators of malicious activity beyond authentication events.

---

## 9. SIEM Integration

The Wazuh agent:

* Collects system and network logs
* Forwards them to the Wazuh manager
* Enables correlation between different attack stages

This ensures visibility across:

* Reconnaissance
* Exploitation
* Post-exploitation

---

## 10. Security Relevance

System and network logs are critical for detecting:

* Port scanning and reconnaissance
* Suspicious outbound connections
* Unauthorized command execution
* Firewall-triggered responses

These logs complement authentication logs to provide **complete attack visibility**.

---

## 11. Detection Readiness

This phase confirms that:

* Multiple log sources are active and monitored
* Different attack types generate distinct log patterns
* Data is available for correlation and advanced detection

This prepares the environment for **SIEM detection and rule engineering**.

---

## 12. Evidence Collection

Screenshots were captured to validate:

* Real-time system log monitoring
* Nmap scan activity
* Reverse shell behavior
* Firewall blocking events

> **Note:** Store images inside the repository and reference them using relative paths.

---

## 13. Conclusion

This phase validates that system-level and network activity logs are successfully generated and monitored.

The results demonstrate:

* Visibility into reconnaissance and execution phases
* Successful logging of attacker behavior
* Effective firewall response logging

Together with authentication logs, this completes the **log collection layer** of the SOC workflow.

---

## 14. Supporting Evidence

![System Logs](../GITHUB/ubnt-ssh-raw.png)

![UFW Logs](../GITHUB/ubnt-ssh-raw2.png)

![Reverse Shell Logs](../GITHUB/ubnt-ssh-raw4.png)

---
