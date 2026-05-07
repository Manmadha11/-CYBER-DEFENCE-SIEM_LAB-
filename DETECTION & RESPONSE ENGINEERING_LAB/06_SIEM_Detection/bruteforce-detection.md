# SIEM Detection – SSH Brute Force Alert Validation

---

## 1. Overview

This phase validates the SIEM platform’s ability to detect brute force authentication attempts based on log data collected from the monitored endpoint.

Detection validation ensures that security events are not only logged but also **analyzed, correlated, and escalated as alerts**.

---

## 2. Objective

The objective of this phase is to:

* Confirm successful detection of SSH brute force activity
* Validate Wazuh rule-based alert generation
* Analyze alert data for accuracy and completeness
* Ensure the SIEM detection pipeline is functioning correctly

---

## 3. Detection Scenario

During the attack simulation phase:

* Multiple failed SSH login attempts were generated
* Logs were collected from the Ubuntu endpoint (`/var/log/auth.log`)
* The Wazuh agent forwarded these logs to the manager

The Wazuh SIEM applied built-in detection rules to identify brute force behavior.

---

## 4. Detection Method

Detection was performed using the **Wazuh Dashboard** by querying relevant alerts.

### Query Used

```text id="q1z8dn"
agent.name: ubuntu AND rule.id: 5716
```

### Query Explanation

* `agent.name: ubuntu` → Filters events from the target endpoint
* `rule.id: 5716` → Wazuh rule for multiple SSH authentication failures

This query isolates brute force-related alerts for analysis.

---

## 5. Detection Results

The SIEM platform successfully generated alerts indicating:

* Multiple failed login attempts
* Repeated authentication failures from a single source IP
* Automated attack behavior

Alert data included:

* Timestamp
* Source IP address
* Target username
* Rule ID and severity level

---

## 6. Alert Analysis

The alerts clearly show:

* High-frequency login failures
* Consistent attacker IP (e.g., 192.168.239.6)
* Targeting of privileged accounts (e.g., root)

The detection rule triggered after a threshold of failed attempts, confirming **pattern-based detection logic**.

---

## 7. Rule Details

* **Rule ID:** 5716
* **Description:** SSH brute force attack detected
* **Trigger Condition:** Multiple authentication failures within a defined time window

This rule is part of Wazuh’s default detection set for SSH monitoring.

---

## 8. Security Significance

Detecting brute force attacks is critical because:

* It prevents unauthorized access attempts
* It identifies credential-based attacks early
* It enables rapid defensive response (e.g., IP blocking)

Early detection reduces the risk of system compromise.

---

## 9. Detection Validation

This phase confirms that:

* Logs are correctly ingested by the SIEM
* Detection rules are functioning as expected
* Alerts accurately represent malicious activity

This validates the **end-to-end detection pipeline**.

---

## 10. Evidence Collection

Screenshots were captured to demonstrate:

* Wazuh dashboard alerts
* Filtered query results
* Authentication-related event logs

> **Note:** Store all images inside the repository and use relative paths.

---

## 11. Conclusion

This phase confirms that the Wazuh SIEM successfully detects SSH brute force attacks using built-in rules.

The results demonstrate:

* Effective log collection
* Accurate event correlation
* Reliable alert generation

The environment is now ready for **custom detection rule development and advanced detection engineering**.

---

## 12. Supporting Evidence

![SIEM Dashboard Logs](../images/logs-w.png)

![Agent Logs](../images/logs-A.png)

![Auth Log Evidence](../images/logs-a2.png)

![Agent Logs](../GITHUB/wzh-ssh-brut-id.png)

![Agent Logs](../GITHUB/wzh-ssh-brut-id2.png)

---
