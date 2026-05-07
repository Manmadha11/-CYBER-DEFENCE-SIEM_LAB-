# Log Collection – Authentication Monitoring

---

## 1. Overview

This phase focuses on monitoring authentication logs on the target system to validate that simulated attacks generate observable security events.

Log collection is a fundamental component of Security Operations, enabling visibility into system activity and forming the basis for threat detection and analysis.

---

## 2. Objective

The objective of this phase is to:

* Monitor authentication logs in real time
* Verify that attack simulations generate log data
* Identify patterns associated with brute force activity
* Confirm that logs are available for SIEM ingestion

---

## 3. Log Source

Authentication logs from the **Ubuntu server** were used as the primary data source.

These logs record:

* Login attempts
* Authentication failures
* User activity
* Source IP addresses

File location:

```bash id="f8y2hk"
/var/log/auth.log
```

---

## 4. Monitoring Method

Real-time monitoring was performed to observe log generation during attack execution.

### Command Used

```bash id="k3d9wp"
sudo tail -f /var/log/auth.log
```

### Command Explanation

* `sudo` → Required to access restricted log files
* `tail -f` → Continuously displays new log entries
* Enables live observation of system activity

---

## 5. Observations

During the SSH brute force simulation:

* Multiple failed login attempts were recorded
* Entries included timestamps, usernames, and source IP
* Repeated authentication failures were observed in short intervals

Example log pattern:

```text id="a7v2nc"
Failed password for root from 192.168.239.6 port 60130 ssh2
```

These repeated failures clearly indicate brute force behavior.

---

## 6. Log Analysis

Key indicators identified:

* High frequency of failed login attempts
* Consistent source IP address (attacker machine)
* Targeting of privileged accounts (e.g., root)

These patterns align with common brute force attack signatures.

---

## 7. SIEM Integration

The Wazuh agent installed on the Ubuntu system:

* Collects authentication logs
* Forwards them to the Wazuh manager
* Enables centralized analysis and alert generation

This confirms that the **log pipeline is functioning correctly**.

---

## 8. Security Relevance

Monitoring authentication logs is essential for detecting:

* Brute force attacks
* Unauthorized login attempts
* Credential abuse
* Suspicious access patterns

Early detection helps prevent account compromise and system intrusion.

---

## 9. Detection Readiness

This phase validates that:

* Logs are being generated correctly
* Relevant security events are captured
* Data is available for SIEM detection rules

It serves as the foundation for the **SIEM Detection phase**.

---

## 10. Evidence Collection

Screenshots were captured to demonstrate:

* Real-time log monitoring
* Authentication failure events
* Attack-generated log entries

> **Note:** Store images inside the repository and use relative paths.

---

## 11. Conclusion

This phase confirms that authentication logs are successfully generated and monitored during attack simulation.

The presence of detailed log data ensures that the SIEM platform can:

* Detect malicious activity
* Correlate events
* Trigger alerts

The environment is now fully prepared for **detection engineering and alert validation**.

---

## 12. Supporting Evidence

![Wazuh Logs](../images/w-logs.png)

![System Logs](../images/logs-w2.png)

![Agent Logs](../images/logs-A.png)

![Auth Log](../images/auth-log.png)

![Additional Logs](../images/logs-a2.png)

---
